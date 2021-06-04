# mmc-utils

## Install cross compile tool
```
sudo apt install gcc-arm-linux-gnueabi
```

## Compile
```
cd mmc-utils
make
```

## Install to any android evb
```
adb root
adb push mmc /data/
adb shell chmod +x /data/mmc
```

## Examples
* mmc help command
```
# adb root
# adb shell /data/mmc --help
Usage:
        mmc extcsd read <device>
                Print extcsd data from <device>.
        mmc writeprotect boot get <device>
                Print the boot partitions write protect status for <device>.
        mmc writeprotect boot set <device> [<number>]
                Set the boot partition write protect status for <device>.
                If <number> is passed (0 or 1), only protect that particular
                eMMC boot partition, otherwise protect both. It will be
                write-protected until the next boot.
```

* send cmd6 to flush cached
```
# adb root
# adb shell /data/mmc cmd6 /dev/block/mmcblk1 32 1
Going to send cmd6, index: 0x20, value: 0x1
```

* RPMB write key
```
rk3399_box:/ # /data/mmc rpmb write-key /dev/block/mmcblk1rpmb  -
abcdefghijklmnopqrstuvwxyz123456
rk3399_box:/ #
```

* RPMB read counter
```
rk3399_box:/ # /data/mmc rpmb read-counter /dev/block/mmcblk1rpmb
Counter value: 0x00000000
```


