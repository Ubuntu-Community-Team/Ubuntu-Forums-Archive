---
title: "Ubuntu - Win7 dual boot help"
date: 2012-03-11
forum: General Help
---

### Post by Sophin87 on 2012-03-11
Hey all,

I'm trying to dual boot ubuntu 11.10 and Win7 but I'm running into some problems.

First of all, I'm trying to install Win7 after having installed Ubuntu. I realized I needed Win7 for some work-related programs after having installed Ubuntu. Seeing as I've had this laptop for a few months now, I don't really want to reinstall the whole thing.

Now, I've managed to install windows and restored my MBR so I'm back in ubuntu again. However, I'm having problems setting up GRUB to allow me to dual boot.
There's quite a number of guides online, but most are old and even more are confusing. Can someone give me a step-by-step on how to set up my grub?

Some info:
Ubuntu 11.10 installed to /sda1
Windows 7 ultimate installed to /sda2

I restored grub by booting into a liveCD and reinstalling grub from the cd.

I could really use some help. This is basically the last step in the installation and I'm kind of lost!

Cheers in advance!

---

### Post by 2F4U on 2012-03-11
Not sure at what information or tutorials you looked, but the Ubuntu community documentation is up-to-date and covers your case:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by akshay.sulakhe on 2012-03-11
well,i really dont understand what the problem is. Go in the Ubuntu system,use the command update-grub and it should be fine. If you are unable to go in the system,boot a live cd,chroot in the system,u can find how to chroot in documentation,just 2 commands,and then give update-grub.  
Commands,use this with a live cd :-
sudo -i
mount /dev/sda1 /mnt   ..assuming sda1 is ur ubuntu drive
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit

Give the commands as they are,dont change anything.jsut the sda u know that i guess. :-) Hope it helps.

---

### Post by oldfred on 2012-03-11
If you have already restored grub2's boot loader to the MBR, you do not have to chroot into your system, but just update grub. That runs the os-prober that will find other operating systems.

```
sudo udpate-grub
```If not restored, you usually do not have to chroot, but may if major issues:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

edit:
rereadin [akshay.sulakhe]("http://ubuntuforums.org/member.php?u=683105") post he mention the update grub, I guess I am just clarifying it a bit.

---

### Post by Sophin87 on 2012-03-11
Thanks for helping me.

2F4U: I've been following that guide, but I'm kind of stuck on getting a boot menu allowing me to select windows or ubuntu. After installing windows I rebooted linux on the livecd and reinstalled grub, which restored the MBR to allow me to boot to linux again.
Now, I'm stuck trying to get the dualboot menu to work.



I'm running into the following problem when trying to update or chroot grub:

/etc/default/grub: 14: menuentry: not found

---

### Post by ohadcn on 2012-03-11
install startupmanager
configure the menu as you want (has graphic interface)

---

