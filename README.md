# motorola_one_power_root_plus
how i rooted my motorola and installed linux in it.


### `Steps to root`
* Note you will lose all data, so back up everything before doing any of the steps *
- unlock bootloader
  - link: https://forum.xda-developers.com/t/guide-motorola-one-power-unlock-relock-bootloader-flashing-custom-recovery-rooting.3858797/ 
  - `$ fastboot oem get_unlock_data`
  - `$ fastboot oem unlock EBK4NJO35ISPQTNGYWGO`
- get stock boot.img file from devices
  - https://www.droidwin.com/extract-boot-img-directly-from-device-without-downloading-firmware/
  - below are commands from link
   ```
     $ adb reboot recovery
     $ adb shell
     $ dd if=/dev/block/bootdevice/by-name/boot of=/sdcard/boot.img
     $ exit
     $ adb pull /sdcard/boot.img stock_boot.img
 - Once your device boots up, install the Magisk App and patch this boot.img file via it. Doing so shall give you the magisk_patched.img file, which you could then flash via Fastboot Commands and hence root your device!  https://topjohnwu.github.io/Magisk/install.html#patching-images 
   - `$ adb pull /sdcard/Download/magisk_patched_[random_strings].img`
 - Flash the magisk.zip file https://www.youtube.com/watch?v=xfdfZq-h20k
 - Flash the magisk_patched file
   - `$ fastboot flash boot /path/to/magisk_patched.img`
 - reboot
 - confirm in magisk app, everything is installed fine
 - confirm using root checker app root is enabled, (grant access in the pop up or in the magisk app)

#### Mistakes:
I did lot of mistakes leading to non roots, boot stuck in android logo, boot stuck in TWRP (that was scary) and some more i don't remember.  
I recovered by booting to recovery and do factory reset data and then start over.  
Note TWRP imsage cannot be flashed in motorola one, instead we just boot temporarily in that.  

