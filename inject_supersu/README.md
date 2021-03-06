# Steps to get permanent root on Kyocera KC-S701

**Be careful! This procedure can brick your phone!**

**These scripts were tested on 102.0.1920 firmware**

**Don't run OTA updates after you've installed SuperSU! This will brick your phone!**

These scripts should be executed on Linux based OS. I.e. [Ubuntu](https://www.ubuntu.com/download/desktop). You can flash USB drive under Windows following the [instructions](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows).

* Download SuperSU ZIP archive: http://www.supersu.com/download
* Download Busybox ZIP archive: https://forum.xda-developers.com/android/software-hacking/tool-busybox-flashable-archs-t3348543
* The `./reboot_into_dload.sh` script will reboot your phone into download mode.
* Fetch original system parition from the phone: `sudo ./read_system_partition.sh`
* Run `sudo ./install_su.sh` script to inject SuperSU into the Kyocera system partition: `19-system-root.img`
* This partition could be flashed into the phone using the command: `sudo ./write_rooted_system.sh`
* When the script is finished, reboot the phone using its power button. You have to hold it till vibration.
* You'll get installed SuperSU and possibility to write into the external sdcard.

# Additional info

You can spoof `wlan` module by `mmc_protect_as_wlan.ko` in order to be able to disable the write protection. [More details](https://github.com/hiikezoe/android_mmc_protect).
After flashing the modified system partition you can disable system partition write protection by executing the following commands:

```sh
adb shell
su
disable-security.sh
read-write.sh
```

Last command can hang, in this case just reboot the phone and try to execute all the commands again.

# Licence

`mmc_protect.ko` and `mmc_protect_as_wlan.ko` were compiled using this source code: https://github.com/hiikezoe/android_mmc_protect which is licensed under GPLv2.
