---
title: "Grub error? New to Ubuntu"
date: 2010-11-06
forum: General Help
---

### Post by sageface on 2010-11-06
Hey yall.
I'm new to Ubuntu after a friend showed me the system but now I can't get it to work. I've put the ISO onto a disc and rebooted, selected Ubuntu as a startup option but then it comes up with this error message:
'Error: No such device /ubuntu/disks/roots'
It displays about 3 of these error messages and then I'm left with an abyss of entering commands through something called 'Grub'.
I've looked everywhere for some sort of contribution to my problem but so far nothing has helped. Please help me!

---

### Post by wilee-nilee on 2010-11-06
> **sageface said:**
> Hey yall.
I'm new to Ubuntu after a friend showed me the system but now I can't get it to work. I've put the ISO onto a disc and rebooted, selected Ubuntu as a startup option but then it comes up with this error message:
'Error: No such device /ubuntu/disks/roots'
It displays about 3 of these error messages and then I'm left with an abyss of entering commands through something called 'Grub'.
I've looked everywhere for some sort of contribution to my problem but so far nothing has helped. Please help me!

Sounds like a wubi install=from a live windows environment. Can you give a more detailed description of the operating systems on the computer and exactly how you installed if this is what you did.

---

### Post by sageface on 2010-11-06
I downloaded the Ubuntu Netbook 10.10 ISO and used PowerISO to burn the files onto a disk. I then rebooted my computer, selected Ubuntu and then got the error message.
I'm on Windows 7 and trying to install Ubuntu onto my 1TB external hard drive.

---

### Post by wilee-nilee on 2010-11-06
> **sageface said:**
> I downloaded the Ubuntu Netbook 10.10 ISO and used PowerISO to burn the files onto a disk. I then rebooted my computer, selected Ubuntu and then got the error message.
I'm on Windows 7 and trying to install Ubuntu onto my 1TB external hard drive.

You should burn it as a image, it sounds like a data burn.
Also be sure to resize the W7 partitions with its disk manager, leaving a open space for your install.

You can check the MD5sum of the ISO, and the CD if you did burn a image.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It is rather strange that you would be seeing anything grub with a install disc, your W7 boots like normal right?

---

### Post by sageface on 2010-11-06
> **wilee-nilee said:**
> You should burn it as a image, it sounds like a data burn.
Also be sure to resize the W7 partitions with its disk manager, leaving a open space for your install.

You can check the MD5sum of the ISO, and the CD if you did burn a image.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It is rather strange that you would be seeing anything grub with a install disc, your W7 boots like normal right?

Honestly, my W7 is completely stable. Ubuntu is just acting up. I checked MD5sum and everything seems to be okay. How do i burn the ISO as an image rather then a data burn?

---

### Post by wilee-nilee on 2010-11-06
> **sageface said:**
> Honestly, my W7 is completely stable. Ubuntu is just acting up. I checked MD5sum and everything seems to be okay. How do i burn the ISO as an image rather then a data burn?
 
Just right click the ISO in windows and burn to disc the stock cd writer should do it. If you can control the burn speed; generally in the past it was advised to be around 4x but I haven't had a bad burn in a while with whatever the burners slowest speed is, if you can choose.

I will transfer a ISO over to my W7 set up and confirm this .

Power ISO should work as well I haven't used it for a while but look for a image burn in the panel.

If you have a thumb drive I would use that it will run better in all ways due to the flash type memory. Here is a thumb loader.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

So in my W7 set up there is a burn disc image in the right click on the ISO.

---

### Post by sageface on 2010-11-06
> **wilee-nilee said:**
> Just right click the ISO in windows and burn to disc the stock cd writer should do it. If you can control the burn speed; generally in the past it was advised to be around 4x but I haven't had a bad burn in a while with whatever the burners slowest speed is, if you can choose.

I will transfer a ISO over to my W7 set up and confirm this .

Power ISO should work as well I haven't used it for a while but look for a image burn in the panel.

If you have a thumb drive I would use that it will run better in all ways due to the flash type memory. Here is a thumb loader.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

So in my W7 set up there is a burn disc image in the right click on the ISO.


It's funny, my brother just recommended UNetbootin as well. Unfortunately, I don't have a flash drive at this time. I'll go look for one.

With PowerISO, would 'Hard Disc Image' be the suitable burn process?

---

### Post by wilee-nilee on 2010-11-06
> **sageface said:**
> It's funny, my brother just recommended UNetbootin as well. Unfortunately, I don't have a flash drive at this time. I'll go look for one.

With PowerISO, would 'Hard Disc Image' be the suitable burn process?

The website under main features says images so I don't really know if the disc image is correct. The right click though on the ISO will get the in house burn image done.
[http://www.poweriso.com/](http://www.poweriso.com/)

You generally never extract the Ubuntu ISO unless you want to tweak it, it is just a ISO image to be burned as is. It looks like the PowerISO does a lot of things, like extracting.

---

