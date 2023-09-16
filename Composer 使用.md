# Composer 使用

## 你不知道的 composer

### 查看帮助

```bash
# 列出所有命令
composer list
composer update -h
composer self-update -h
```

### 自更新

```bash
composer self-update --stable
composer self-update --2.2
```

### 全局更新

```bash
composer global update -v
```

### 全局删除一个依赖

场景：切换 php 版本后，php-cs-fixer 版本冲突了(3.4.0 以后的版本都不支持 php7.2 了)，但是全局更新命令后还是报错
这时就只能删了重装（或者也可以使用`composer global reinstall`）

```bash
# 正常删除时，会同时更新依赖，如果不希望更新依赖，或者更新依赖时报错（比如切换了 php 版本后，有些依赖就会有版本冲突），这时，可以加上 --no-update
# 但这样不会删除 vendor 下的实际包文件，也不会更新 lock 文件
composer global remove friendsofphp/php-cs-fixer --no-update && composer global update --lock
composer global require friendsofphp/php-cs-fixer
```

### 只更新锁文件

场景：当锁文件报不匹配的错时

```bash
composer global update --lock
```

### 不发生实际操作，只输出报表

composer global update --dry-run

### 列出所有依赖

```bash
# 查看所有依赖
composer global show
# 查看最顶层依赖
composer global show --self
```

