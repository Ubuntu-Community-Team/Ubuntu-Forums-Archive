---
title: "Problems with grub&gt;rescue"
date: 2011-08-18
forum: General Help
---

### Post by franchzilla on 2011-08-18
Hello,

It's my frist time around here. I currently own a Sony Vaio FX running on Windows 7 and Ubuntu. Recently, I tried to delete one partition from my computer and since then, when I try to boot it , I get a message: 

unknown filesystem
grub>rescue

I tried using the ls command and I get: 

(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)

I don't know which one is my boot partition. I tried using some commands to run grub in normal mode, but all I get is the message of "unknown filesystem again".

So I tried running Ubuntu from the flashdrive I used to install it. I found many solutions to this problem, like:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459](http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459)
[http://ubuntuforums.org/showthread.php?t=1417672](http://ubuntuforums.org/showthread.php?t=1417672)
[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/)

But none of them worked. Does anyone know what's going around? I just can't seem to solve this.

Thank you,
Daniel Franch

Edit:
Oh! Some of these solutions that depend on using ubuntu's terminal don't work with me because I don't know which is my boot partition and I don't know how to find it. I tried fdisk -l, but nothing appears.

---

### Post by garvinrick4 on 2011-08-18
#Use a live Cd (your install cd using Try Ubuntu) (or your live USB using Try Ubuntu)
#Open a terminal (ctrl/alt/t)
```
sudo fdisk -l
``` (lower case L)
Pick out your linux install.
#Most likely sda5, (not the one that says swap) will just say linux
Will give you sda5 for this example use your own.
#Now run this:
```
grub-install -v
```If it says 1.98 copy and paste below one at a time: (ubuntu 9.10 to 10.10)
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo reboot
```#If when ran 
```
grub-install -v
```If It says 1.99 run this code below one at a time, copy and paste.(ubuntu 11.04 to 11.10)
```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
sudo umount /mnt
sudo reboot
```
Once booted into Ubuntu:
open a terminal and run:
```
sudo update-grub
```
Will put Windows in as a boot entry for you.

---

### Post by raja.genupula on 2011-08-18
> **franchzilla said:**
> Hello,

It's my frist time around here. I currently own a Sony Vaio FX running on Windows 7 and Ubuntu. Recently, I tried to delete one partition from my computer and since then, when I try to boot it , I get a message: 

unknown filesystem
grub>rescue

I tried using the ls command and I get: 

(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)

I don't know which one is my boot partition. I tried using some commands to run grub in normal mode, but all I get is the message of "unknown filesystem again".

So I tried running Ubuntu from the flashdrive I used to install it. I found many solutions to this problem, like:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459](http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459)
[http://ubuntuforums.org/showthread.php?t=1417672](http://ubuntuforums.org/showthread.php?t=1417672)
[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/)

But none of them worked. Does anyone know what's going around? I just can't seem to solve this.

Thank you,
Daniel Franch

Edit:
Oh! Some of these solutions that depend on using ubuntu's terminal don't work with me because I don't know which is my boot partition and I don't know how to find it. I tried fdisk -l, but nothing appears.


to find at what sda you have installed first boot from live cd/usb then do this in terminal


```
sudo os-prober
```

its going to give you at what sda you have installed your OS with its version also

---

### Post by franchzilla on 2011-08-18
That solved the issue. Thanks, guys! :)

---

### Post by garvinrick4 on 2011-08-18
In the upper right in Thread tools can you mark as solved please so others with
same can benefit also. Enjoy your Ubuntu.

---

