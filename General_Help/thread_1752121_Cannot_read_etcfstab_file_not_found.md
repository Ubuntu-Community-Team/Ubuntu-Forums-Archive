---
title: "Cannot read /etc/fstab: file not found"
date: 2011-05-07
forum: General Help
---

### Post by jackantares on 2011-05-07
Hello,

I'm trying to unninstall GIMP, then a power outage makes the computer shut down. After that I think /etc/fstab is corrupted. In Initramfs i get:

mount:
Cannot read /etc/fstab: No such file or directory
mount: Mounting /root/dev on dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

I have seen many solutions in other threads, but my cd drive is not working, so i cant use the live cd, and i dont know why, i cant boot from a flash drive...
I cant format cause I have important data.
Someone help me plz =S

Thanks in advance!

---

### Post by lmarmisa on 2011-05-07
Connect the flash drive and enter the BIOS menu on startup. Check if you are able to define this device as the highest priority boot device.

---

### Post by jackantares on 2011-05-07
Yes, i can make that, but instead of boot, appears just a underline in a black screen, and nothing happens. I've tried before with another flash drive, but a message "Remove media or disk" appears, i think because that device is not bootable. I tried with this second flash drive, then it seems to allow boot, but nothing happens...

---

### Post by jackantares on 2011-05-07
I've tried to boot from a previous version of ubuntu in the GRUB menu, but the same occurs... 
PS: I'm using Lucid 10.04

---

### Post by lmarmisa on 2011-05-07
You have to prepare a reliable Ubuntu Live USB. I suppose you have a second computer from you are posting your messages. Which operating system has this computer?.

---

### Post by jackantares on 2011-05-07
Oh, I forgot to say, I'm using dual boot with windows 7. But, how I can make this reliable live pen drive? I've just copied the content from the CD I've used to install Ubuntu to the pendrive... This CD was burned with the ISO from Ubuntu site...

---

### Post by jackantares on 2011-05-07
I have another computer here with Fedora 14 too (if this can help)

---

### Post by synapsys on 2011-05-07
It sounds like what you need to do is remove the hard drive and install it in another machine in order to get the data off. Why is your CD drive not working? Did you have a surge protector on this computer? It sounds like you may have some damaged hardware...

You can rebuild the /etc/fstab file but it's probably not the only file that's missing.

---

### Post by matt_symes on 2011-05-07
Hi

You can create a bootable USB using unetbootin in windows

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You will want to download the ISO again from Ubuntu's web site as copying the files across from the CD to the USB will not work the way you are trying it.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Once you have a bootable USB we can see what shape your system is in.

Kind regards

---

### Post by lmarmisa on 2011-05-07
> **jackantares said:**
> Oh, I forgot to say, I'm using dual boot with windows 7. But, how I can make this reliable live pen drive? I've just copied the content from the CD I've used to install Ubuntu to the pendrive... This CD was burned with the ISO from Ubuntu site...

If you simply copy all files from a Live CD to a flash drive you will fail to get a Live USB. You should use a program as UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by jackantares on 2011-05-07
I don't have a surge protector. Well, I don't know exactly why it is not working... When I put a CD in Windows, the OS display the cursor with a CD (I think this means that Windows recognize the cd driver), but after that it stops reading... I think it is a problem with drivers... Some days ago it was working (not perfectly, but was working).
I don't know if the fstab is the only file needed, but I can try to recover it, how can I do that?

---

### Post by jackantares on 2011-05-07
so, I will try to do this live USB. Thanks you all!

---

### Post by matey3 on 2011-05-07
Once I had this problem (with older version) but most of the files were not showing up and I could not boot normally so I used fsck -p  and it fixed it.
you have to boot in a single user mode / recovery mode(I hope you still can) then use the fsck -p to fix errors.

---

### Post by matt_symes on 2011-05-07
Hi

One of us should have asked. Is this a partition install or a WUBI install ?

Kind regards

---

### Post by jackantares on 2011-05-07
It's a partition install. I can't boot in recovery mode too =/ I just can boot on Win7 that is in /dev/sda1

---

### Post by lmarmisa on 2011-05-07
I recommend to prepare a Ubuntu Live USB and then run Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jackantares on 2011-05-07
I have prepared the Live USB using the UNetBootin, the menu with installing options appears. I have selected "Try Ubuntu without install". Then the Ubuntu logo and a loading bar has appeared, and nothing happened after that... I waited several minutes, but it seemed like nothing was happening... :/
Is there any command that I can do in the Initramfs to show my partitions or to fix the fstab file?

---

### Post by jackantares on 2011-05-07
I have tested the Live USB in another computer and it works.

---

### Post by jackantares on 2011-05-07
Solved. Thanks you all. I followed this instructions:

[http://ubuntuforums.org/showthread.php?p=10784861#post10784861](http://ubuntuforums.org/showthread.php?p=10784861#post10784861)

I have created a Live USB from Ubuntu Recover Remix for Lucid in 

[http://ubuntu-rescue-remix.org/node/466](http://ubuntu-rescue-remix.org/node/466)

Listed the partitions with

sudo fdisk -l /dev/sda

Then I made a file system check with

sudo fsck -yv /dev/sda4

(/dev/sda4 because is the partition corrupted in my case)


Very grateful for the forum help!! (=

---

