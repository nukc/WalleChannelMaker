# WalleChannelMaker

> ```
> 解决应用加固导致 Walle 渠道信息失效的自动化脚本工具
> ```



## Intention

用了 [ProtectedApkResignerForWalle](https://github.com/Jay-Goo/ProtectedApkResignerForWalle)，但对于自己的需求过于麻烦，动动手解决繁琐。



## Usage

把 `channel.text` `channelmaker.py` `walle-cli-all.jar` 3个文件拷贝到 app 项目根目录下

- `channel.text` 定义渠道信息，一行一个

- `walle-cli-all.jar` 为 walle 渠道打包 CLI 工具

- `channelmaker.py` 使用之前，需要修改此文件里的几个变量

  - ```python
    # 如下几个变量需要自己填写
    
    zipalign = "zipalign"
    apksigner = "apksigner"
    keystore = "xxx.jks"
    key_alias = "xx"
    keystore_password = "xx"
    key_password = "xxx"
    
    walle_cli = "walle-cli-all.jar"
    ```

准备就绪后，可直接执行 `channelmaker.py` ，这样会对项目下 `app/build/outputs/apk` 里的除 debug 的 apk 进行打包，包括进行了 `productFlavors` 配置打包的。

如果需要单独对某个 `productFlavors` 进行渠道打包，加参数 `--flavor=` ：

```sh
channelmaker.py --flavor=google
```

