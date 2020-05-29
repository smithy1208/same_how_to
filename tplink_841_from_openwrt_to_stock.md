# tl-wr841n-v13

## Прошивка на openwrt через tftp.

Скачать

https://downloads.openwrt.org/releases/18.06.7/targets/ramips/mt76x8/openwrt-18.06.7-ramips-mt76x8-tl-wr841n-v13-squashfs-tftp-recovery.bin

Переименовать в tp_recovery.bin выкладываем на tftp-server.

На компе задать IP 192.168.0.66/24


Зажать RESET, включить питание

Удобно пользоваться wireshark, чтобы смотреть что происходит. После перезагрузки роутер с openwrt доступен по 192.168.1.1.
root / no_password


## Венуть на сток!

Вернуть с 19.ХХ.Y релиза не получилось.
Поэтому перешиваем с sysupgrade на 18.06.7

sysupgrade -v /tmp/openwrt-18.06.7-ramips-mt76x8-tl-wr841n-v13-squashfs-sysupgrade.bin

От стоковой прошивки нужно отрезать boot. [Скачать tplink.bin](https://github.com/smithy1208/same_how_to/raw/master/tplink.bin)

dd if=orig.bin of=tplink.bin skip=257 bs=512

Затем так же через sysupgrade 

sysupgrade -v /tmp/tplink.bin

или через tftp

cp tplink.bin tp_recovery.bin
