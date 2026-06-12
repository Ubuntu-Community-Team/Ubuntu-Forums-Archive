---
title: "grub - windows 7 wont boot"
date: 2010-03-21
forum: General Help
---

### Post by UglieFrog on 2010-03-21
I had to reinstall ubuntu last night. Now when I select windows from the grub menu, all i get is a flashing underscore in the top left hand side.



Is there a way to salvage everything with out having to reinstall windoes and ubuntu

---

### Post by nechus on 2010-03-21
I think I read something like this in another thread, and they mentioned the System Rescue CD. You can download it from [http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)

You might have to reinstall GRUB. Please post the solution when you get it. It's an interesting topic.

---

### Post by UglieFrog on 2010-03-21
I dont know how to reinstall grub. 

Is it something I can copy and paste into the terminal

---

### Post by kio_http on 2010-03-21
Try autoreconfiguring Grub with

```
sudo update-grub
```

If it still doesn't work, restore the Windows boot loader, by using StartUp repair under Rescue my System in your Windows 7 Setup disk. Then under Windows 7 Use EasyBCD **2 BETA** (it has to bet version2) and add an entry in the Windows boot loader for Grub2.

---

### Post by 2hot6ft2 on 2010-03-21
Section 16 of this guide should help you out.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It's the grub 2 guide

---

### Post by 2hot6ft2 on 2010-03-21
> **UglieFrog said:**
> I dont know how to reinstall grub. 

Is it something I can copy and paste into the terminal
This is assuming you have grub 2 since you never said what version of ubuntu you're using
From the grub 2 guide again with slight changes

Using Ubuntu 9.10 livecd
Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
```
sudo -i
```
To find out what your partitions are run
```
fdisk -l
```
then using that info run
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by UglieFrog on 2010-03-21
I followed the steps above now it boots to unknown 

With prompt that says

grub rescue>

---

### Post by tophill on 2010-03-25
The same thing just happened to me, after an update that included a Grub 2update.  Grub menu loads fine, and I can load Ubuntu, but Windows 7 option will no longer load.  grub.cnf looks OK, I've run "sudo update-grub" several times. I hadn't run Windows 7 for a few days, but don't think anything got changed there.  I'd rather not run Windows rescue software if I don't have to, since I suspect it's likely to mess up Grub and access to Ubuntu, which is far more important to me.  Any ideas?

---

### Post by andrewthomas on 2010-03-25
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
First see the above link for instructions to restore the win 7 bootloader.
 
Next, restore ubuntu's grub2 by booting to the liveCD. It is a good thread. Just make sure you do it in the right order.

---

### Post by tophill on 2010-03-25
Thanks to andrewthomas -- applying his suggestion fixed my problem pronto!

---

### Post by ProfessionalOPs on 2010-03-25
repairing windows boot was such an awsome addition to windows 7............good job windows.....finally........

---

