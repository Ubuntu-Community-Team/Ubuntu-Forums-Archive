---
title: "Ubuntu CD not working"
date: 2011-04-17
forum: General Help
---

### Post by tushicomeng on 2011-04-17
I downloaded the Ubuntu desktop 10.10 edition twice.
I have created CD from both the images. None of them is working.

I have downloaded the disc images from Ubuntu site only, so there should be no problem in the images and I have made other CDs from my computer which are working fine.

What can be the possible error?
Is there some problem with 10.10 edition?

---

### Post by coldraven on 2011-04-17
Did you use the "Burn Image" option when burning the CDs?
In your computer BIOS have you set the boot order to boot from CD before trying to boot from the hard drive?
To check you have to press F10 or maybe F2 or whatever it says when you switch on the PC to enter the Setup routine. Then look in the Boot section.

---

### Post by tushicomeng on 2011-04-18
Actually. It boots from the CD
after I select install ubuntu desktop edition, then the screen with ubuntu written on it comes with loading effect. then there is only some character interface with many errors.

Do I need to do some changes to the system before installation?

---

### Post by Rubi1200 on 2011-04-18
> **tushicomeng said:**
> Actually. It boots from the CD
after I select install ubuntu desktop edition, then the screen with ubuntu written on it comes with loading effect. then there is only some character interface with many errors.

Do I need to do some changes to the system before installation?
Two things to check:

1. integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2. boot options: [http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by polardude1983 on 2011-04-18
Maybe also try burning at a slower speed?

---

### Post by alphaamanitin on 2011-04-18
you can make a quick md5 hash of the cd and check it against the md5 hash given by Conical, that should quickly let you know if they cd is good or not.

AlphaA

---

### Post by anspideog on 2011-04-18
I am having the same problem and it isn't to do with the .iso file.

Currently dual booting a Dell Inspiron 1525 with Visa and Ubuntu and want to move to only use Ubuntu. Have burned the installation CD twice and checked that it is okay. Here's my exact problem:

- I switch off the laptop, insert the CD into the drive and power it on. I am brought to the same (Grub2) screen to select either the Ubuntu or Vista boot. The CD does not boot automatically. More importantly (from what I've been reading here) the F2 / F6 command solution does not exist. I am prompted to hit 'c' to get a command line but I don't know how to boot the CD from the command line. Any help on this appreciated!!

eilish

---

### Post by tushicomeng on 2011-04-19
I tried installing from originalUbuntu disc my friend had.
It gives any errors.
Some are SQUASHFS errors

SQUASHFS error: Unable to read data cache entry
SQUASHFS error: Unable to read page

---

