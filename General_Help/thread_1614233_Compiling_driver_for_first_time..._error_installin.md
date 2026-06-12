---
title: "Compiling driver for first time... error installing"
date: 2010-11-05
forum: General Help
---

### Post by mal209 on 2010-11-05
Hi everyone,

First-off, let me thank everyone for your previous help, I am quite satisfied with Ubuntu (10.10) now, and only use windows as my DVR (what im currently trying to change).

To that end, i have a Hauppauge 2250 video capture card, and Steven at KernalLabs has an alpha release that has been said to work very well with mythTV.  

Anyways, i followed one of the posts and successfully compiled the driver using "sudo make menuconfig."

I attempted to install with the "make install" command, and the first half of the driver seemed to install and the second half (firmware related) received errors.

make -C firmware install
make[2]: Entering directory `/home/mlavigne/saa7164-v4l/v4l/firmware’
Installing firmwares at /lib/firmware: vicam/firmware.fw cp: cannot stat `vicam/firmware.fw’: No such file or directory
dabusb/firmware.fw cp: cannot stat `dabusb/firmware.fw’: No such file or directory
dabusb/bitstream.bin cp: cannot stat `dabusb/bitstream.bin’: No such file or directory
ttusb-budget/dspbootcode.bin cp: cannot stat `ttusb-budget/dspbootcode.bin’: No such file or directory
cpia2/stv0672_vp4.bin cp: cannot stat `cpia2/stv0672_vp4.bin’: No such file or directory
av7110/bootcode.bin cp: cannot stat `av7110/bootcode.bin’: No such file or directory
make[2]: [install] Error 1 (ignored)

Has anyone seen this error and can you help me out or point me in the right direction? or is this error specific to this driver?

Thanks in advance,
Michael.

---

### Post by jabarker on 2010-11-17
If you are still dealing with this....

I had a functioning myth install with the 2250 driver.  I installed some Ubuntu updates and started getting the errors you found.

I've rebooted, and repeated the installation instructions, and now it's working again.

---

### Post by mal209 on 2011-01-26
did you do anything specific? or just reboot?

---

### Post by mal209 on 2011-01-26
a bit more info:
i recently added "linux-firmware" and can find all the files that are causing problems... they all appear as they should in the /lib/firmware directory.

i have rebooted and retried the install and am still getting the same error.

Thanks in advance,
Michael.

---

