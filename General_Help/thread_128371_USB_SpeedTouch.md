---
title: "USB SpeedTouch"
date: 2006-02-11
forum: General Help
---

### Post by Nyati on 2006-02-11
Hi peeps

I'm not new to attempting to install my Alcatel Speedtouch modem on Breezy Badger, having successfully installed it 11/05. However, after crashing my system this morning, I've attempted reinstalling the modem but find myself at a bottleneck.

I've extracted the firmware for the version 4 modem (ZZZL_3.012) but within the same command provided on [http://www.linux-usb.org/SpeedTouch/ubuntu/](http://www.linux-usb.org/SpeedTouch/ubuntu/), [COLOR="Lime"]unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012 [/COLOR], the command fails and returns a reply of #bash: ./firmware-extractor: is a directory.

Please forgive me for my stupidity in advance, but can somebody please tell me where I'm going wrong.

BTW I have already downloaded and installed the following packages in case they might have given a problem: libatm and br2684ctl

Thanks

---

### Post by ice60 on 2006-02-11
[QUOTE=Nyati]Hi peeps

I'm not new to attempting to install my Alcatel Speedtouch modem on Breezy Badger, having successfully installed it 11/05. However, after crashing my system this morning, I've attempted reinstalling the modem but find myself at a bottleneck.

I've extracted the firmware for the version 4 modem (ZZZL_3.012) but within the same command provided on [http://www.linux-usb.org/SpeedTouch/ubuntu/](http://www.linux-usb.org/SpeedTouch/ubuntu/), [COLOR="Lime"]unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012 [/COLOR], the command fails and returns a reply of #bash: ./firmware-extractor: is a directory.

Please forgive me for my stupidity in advance, but can somebody please tell me where I'm going wrong.

BTW I have already downloaded and installed the following packages in case they might have given a problem: libatm and br2684ctl

Thanks[/QUOTE]
hi, will a picture help you? i hope so.

---

### Post by Nyati on 2006-02-11
Sorry, I presume all these files are in your home folder, but unfortunately the picture doesn't help. I'm trying to split the firmware to produce the 2 files you have at the bottom, otherwise known as: speedtch-1.bin and speedtch-2.bin.

Can anyone help, like I said...the firmware-extractor doesn't seem to work under the following command: 

unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012 

Thanks in advance!

---

### Post by ice60 on 2006-02-11
you can have them if you want?
[http://rapidshare.de/files/13037470/_firmware_files.tar.gz.html](http://rapidshare.de/files/13037470/_firmware_files.tar.gz.html)

MD5
19f33a1b392b32e316d2282d9041e369   firmware_files.tar.gz

---

