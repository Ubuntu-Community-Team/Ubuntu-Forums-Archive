---
title: "[SOLVED] Eee PC 4G"
date: 2009-08-28
forum: General Help
---

### Post by Ciwan on 2009-08-28
Hi Guys

The brother of a friend of mine has sent him an EEE PC from Finland (We are in the UK). The problem is the PC is in Finnish !!

I would like to install Ubuntu onto it ?

Is this possible ? If so .. How does one do it ? Can it be done through a USB Flash Drive ?

I would greatly appreciate any help.

Thank You.

---

### Post by aysiu on 2009-08-28
Yes, it can be done through a flash drive.

All you need is a flash drive with at least 1 GB free space, [UNetBootIn](http://unetbootin.sourceforge.net/), and a downloaded Ubuntu .iso file.

After you've "burnt" the .iso to the flash drive, keep it in, reboot your Eee PC computer, and tap Esc during bootup. That will let you boot from USB.

---

### Post by aysiu on 2009-08-28
Yes, it can be done through a flash drive.

All you need is a flash drive with at least 1 GB free space, [UNetBootIn](http://unetbootin.sourceforge.net/), and a downloaded Ubuntu .iso file.

After you've "burnt" the .iso to the flash drive, keep it in, reboot your Eee PC computer, and tap Esc during bootup. That will let you boot from USB.

---

### Post by Ciwan on 2009-08-29
Hi Aysiu

OK I downloaded UNetBootIn and burnt the Ubuntu ISO onto the flash drive .. then I took it out (to insert it into the EEE PC) and tried installing Ubuntu .. but I get the following

> Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT ! does not exist. Dropping to a shall !

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

Please help :(

---

### Post by bodhi.zazen on 2009-08-29
Sometimes there are problems with the transfer.

First back up any data you wish to keep from the flash drive and reformat it to FAT

Then use unetbootin to "install" the ubuntu .iso to  the flash drive (you do not copy the iso or "burn" it, select the iso in unetbootin).

---

### Post by Ciwan on 2009-08-29
I did format the USB Flash (FAT) before burning the ISO on to it.

And Yes, I used that program to do it. I didn't do Copy/Paste !! :(

---

### Post by bodhi.zazen on 2009-08-29
OK, try deleting all the files off the USB and run unetbootin again.

If it fails a second time check the MD5SUM of the iso, make sure the download was not corrupt.

---

### Post by Ciwan on 2009-08-29
I have just done it again with uNetBootIn but again I get the same error !

How do I check the MD5SUM ?

Thanks

---

### Post by bodhi.zazen on 2009-08-29
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Ciwan on 2009-08-29
Thanks

OK I have just compared and they are the same :(

Now what do I do ?

Are you guys sure Ubuntu can be installed on the Eee 4G ??

Thanks

---

### Post by bodhi.zazen on 2009-08-29
Just to confirm, you are using the "Desktop" iso and not the "Alternate" or another iso ?

32 bit and not 64 bit ?

I have not installed on your computer, but the problem seems to be as it is booting it can not find the files it needs.

You may need to try a different iso, which one are you using ?

---

### Post by Ciwan on 2009-08-29
Yep I am using the Desktop ISO.

And Yes it is 32 bit.

That program uNetBootIn, I have not installed it on the Eee PC ... I don't know if that matters

Also the ISO is on my Desktop PC (Win Vista) and I'm running the uNetBootIn in Vista and burning the ISO onto the flash.

Do I have to do these steps on the Linux OS currently on the Eee PC ??

Thanks

---

### Post by bodhi.zazen on 2009-08-29
> **Ciwan said:**
> Yep I am using the Desktop ISO.

And Yes it is 32 bit.

That program uNetBootIn, I have not installed it on the Eee PC ... I don't know if that matters

Also the ISO is on my Desktop PC (Win Vista) and I'm running the uNetBootIn in Vista and burning the ISO onto the flash.

Do I have to do these steps on the Linux OS currently on the Eee PC ??

Thanks

No, it should work in Vista.

I am sorry you are having this problem, my only advice it to try a different iso :(

---

### Post by Old_Grey_Wolf on 2009-08-29
If you have the eee pc 701 4G, I have been using eeebuntu with success. My wife likes it with the NBR version on her 701. You can get it at [http://www.eeebuntu.org/](http://www.eeebuntu.org/). UNetbootin can put it on a USB for you. You need to select the iso disk image option in UNetbootin.

---

### Post by aysiu on 2009-08-29
> **Ciwan said:**
> 
Are you guys sure Ubuntu can be installed on the Eee 4G ?? Yes. I had an Eee PC 701 (4 GB) for a full year and installed various versions of Ubuntu (and other distros) on it many times successfully.

If you're running into errors, there are only several possible explanations:

1. The .iso got corrupted during the download process
2. The .iso wasn't properly copied over to the USB stick with UNetBootIn for some reason.
3. The USB stick is faulty or not formatted as FAT16 or FAT32

If you have done a proper md5sum check on the .iso and you're sure the USB stick is not faulty and is properly formatted, then erase every single file off the USB stick (including hidden files) and then try UNetBootIn again from scratch.

---

### Post by Ciwan on 2009-08-30
But My Eee PC is 4G

On the sticker underneath it doesn't say Eee PC 701 4G

It ONLY says Eee PC 4G !!!

Are they the same ??

Thanks

---

### Post by aysiu on 2009-08-30
> **Ciwan said:**
> But My Eee PC is 4G

On the sticker underneath it doesn't say Eee PC 701 4G

It ONLY says Eee PC 4G !!!

Are they the same ??

Thanks
There are only so many Asus Eee PCs that came with 4 GB of SSD space: 700 and 701, as far as I know. Actually, the 700 may have been only 2 GB?

It doesn't really matter, anyway. I've never heard of an Eee PC that is unable to boot Ubuntu from USB stick.

---

### Post by winotree on 2009-08-30
> **Ciwan said:**
> But My Eee PC is 4G

On the sticker underneath it doesn't say Eee PC 701 4G

It ONLY says Eee PC 4G !!!

Are they the same ??

Thanks
They are one and the same.  Just like mine says...  ;)

---

### Post by Ciwan on 2009-08-30
Thanks Guys it did it !!!

The reason it was not doing it before was because I was choosing the bottom option !! the OEM or something !

This time I choose Default and it worked !! I now have Great Ubuntu installed on it.

Thank You for ALL YOUR HELP. :) Much APPRECIATED.

THANK YOU.

---

