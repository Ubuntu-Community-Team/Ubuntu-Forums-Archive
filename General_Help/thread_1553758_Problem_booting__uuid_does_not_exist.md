---
title: "Problem booting : uuid does not exist"
date: 2010-08-15
forum: General Help
---

### Post by pimseb on 2010-08-15
Hello,

First of all, sorry for my english. I'm having big issues since 1 month with ubuntu 10.04.
When I boot, sometimes it works, sometimes not. When it's not working, I do see grub, but after one minut, I get a error : "gave up waiting for root device - uuid 5caaaa.... does not exist. Dropping to a shell"
If I'm wrting here it's because I've tried almost everything to fix this error :
- replacing uuid with /dev/sda in fstab
- reinstalling ubuntu 10.04 on the same disk (ssd kingston)
- reinstalling ubuntu 10.04 on another disk (hard drive)
- trying with one DDR3 instead of 2
I thought it was my motherboard (because I had also problems with internal network card). So I changed motherboard, but the result remains the same. I just lost my money...
My conf is : Intel i5 750 + 4Gb DDR3 + motherboard Gigabyte P5-UD4P or my new motherboard Asus P7P55D-E. Video card : Gigabyte 9600 GT.
I have 4 disks installed all in SATA and a DVD in IDE.
Today I tried a new kernel : 2.6.34-020634-generic
But once again, after a reboot I had the same error.
Moreover when ubuntu boots, sometimes I have problems to access to my hard drive (it freezes or slows down). It happened with all my drives and with the 3 motherboards. So finally I don't know where is the problem.
I've installed windows7 "just to see" and so far it seems to work. But I don't want to swith back to seve so maybe I could get help here ? :)
I looked into syslog but I don't see anything because it seems the system doesn't log when it can't boot. Or maybe there's another log ? 
Could the problem come from my /home ? I've saved it and replaced it after new install.
Thanks for reading :)

---

### Post by Ginsu543 on 2010-08-15
Could you type "sudo blkid" without quotes inside Terminal (you'll have to type in your root password) and then post the result here?

---

### Post by oldfred on 2010-08-15
Post this, it also includes the blkid list:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Have you installed the nvidia driver. With 9600gt I had to use nomodeset on first boot, but after installing nvidia driver I have had no issues with video.

You can also check kernel & messages in system, adminstration, log file viewer to see if any thing is slow - long time gap or repeatedly trying to load.

---

### Post by Karl1982 on 2010-08-15
Could the problem be with the grub config?  I know it often lists something like that as a kernel argument, and if you've been shuffling hard drives around, it might've gotten confused.  Something I would try to rule that out would be booting from a disc or flash drive that has grub4dos installed (I usually have a couple handy since I use it often), and then try to jumpstart Ubuntu from the grub4dos command line:

```
find --set-root /vmlinuz
kernel /vmlinuz
initrd /initrd.img

```

That would essentially bypass the GRUB installed on your hard drive.  You could probably also do something similar with isolinux or syslinux if you have one handy.

---

