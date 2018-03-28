# packet

> THANKS：本模块来自 [FastD](https://github.com/fastdlabs/packet)

PHP 数据打包、解包工具，支持二进制，json格式.

### ＃composer

```json
{
    "require": {
        "uniondrug/packet": "~1.1"
    }
}
```

### ＃使用

二进制数据打包的时候程序会将内容加入 “盐(SALT)” 来强化数据安全性，如果需要自定义盐值，需要在实现类中重写 `Uniondrug\Packet\PacketInterface::SALT` 类常量。

##### ＃二进制

```php
use Uniondrug\Packet\Binary;

$origin = ['name' => 'janhuang'];

$data = Binary::encode($origin);
$origin = Binary::decode($data);

/**
 * Array(
 *      "name" => "janhuang"
 * )
 */
```

##### ＃JSON

JSON 数据在打包的时候同样会加入盐值，程序自行追加，并且会对盐值进行在加密，在数据处理解析返回会自动移除盐值，返回纯净数据。因此在传入数据的时候需要注意不要存在 `packet_salt` 字段。

```php
use Uniondrug\Packet\Json;

$origin = ['name' => 'janhuang'];

$data = Json::encode($origin);
$origin = Json::decode($data);

/**
 * Array(
 *      "name" => "janhuang"
 * )
 */
```

### ＃Testing

```
phpunit
```

# License MIT