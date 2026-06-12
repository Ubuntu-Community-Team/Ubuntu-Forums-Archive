---
title: "Complete start-up failure"
date: 2010-11-21
forum: General Help
---

### Post by Cazzer on 2010-11-21
Hello. This is rather urgent, as my computer seems to be completely broken.

I installed Ubuntu. Ubuntu loaded, I had a go with browsing and things, blah blah blah. Then it updated, which seemed to go fine. However, when it restarted, I got the following message:

error: no such device: 36fe47f1-1c97-464c-dacf84591118
grub rescue>_

This is a dual-boot XP and Ubuntu system, but this message appeared *directly at startup.* I did not get a chance to select which OS I wanted to boot, which is why this is rather urgent.

And yes, I am using a different computer to post this message.

---

### Post by dino99 on 2010-11-21
that means that grub dont find the good path. Is ubuntu installed on a removable device ?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://ubuntuforums.org/showthread.php?t=1564448&page=2](http://ubuntuforums.org/showthread.php?t=1564448&page=2)

---

### Post by Cazzer on 2010-11-21
Nope, it's installed on my hard drive. When I updated Ubuntu, I told it to install GRUB on both hard drives (my C: drive is for XP, the D: drive is for Ubuntu.)

---

### Post by Cazzer on 2010-11-21
Nope, it's installed on my hard drive. When I updated Ubuntu, I told it to install GRUB on both hard drives (my C: drive is for XP, the D: drive is for Ubuntu.)

---

### Post by Cazzer on 2010-11-21
Nope, it's installed on my hard drive. When I updated Ubuntu, I told it to install GRUB on both hard drives (my C: drive is for XP, the D: drive is for Ubuntu.)

---

### Post by bcbc on 2010-11-21
You need to reinstall the windows bootloader to the drive MBR. For XP you can insert the windows disk and boot to a repair prompt, then run "fixmbr".

It's also possible to repair if you don't have an XP disc by booting an Ubuntu CD in Live CD mode (select "Try without installing") and installing Lilo (you can ignore the warnings). 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by oboedad55 on 2010-11-21
> **bcbc said:**
> You need to reinstall the windows bootloader to the drive MBR. For XP you can insert the windows disk and boot to a repair prompt, then run "fixmbr".

It's also possible to repair if you don't have an XP disc by booting an Ubuntu CD in Live CD mode (select "Try without installing") and installing Lilo (you can ignore the warnings). 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Lilo? I have to respectfully disagree with this.You may have to fix the old boot record, but I doubt it. In any case, you can do the following to reinstall grub and it should find both OSes. I am a little confused when you say that you installed grub to two hard drives. I didn't know that was possible. If it is, then it should only be installed in one place. 

--

Firstly, boot from your Linux or Ubuntu CD, and choose the option of trying Ubuntu without installation.

After Ubuntu gets loaded from the Live CD, you have to find out that which of the drive or partition was the one, containing your previously installed Linux. For checking out the partitions, goto the terminal ( Applications -> Accessories -> Terminal ), and write:

sudo fdisk -l
or
fdisk -l

This will show you the list of partitions you have in your system.

After you get to know the partition where your Ubuntu was installed, write the following commands. For example, if the partition is /dev/sda1, you have to write the following commands (you have to replace the sda1 from your partition name):

sudo mount /dev/sda1 /mnt
sudo mount –bind /dev /mnt/dev
sudo mount –bind /proc /mnt/proc

Now write:

sudo chroot /mnt

and then install Grub by the following command:

grub-install /dev/sda

If any errors found after entering the above line, then try this one:

grub-install –recheck /dev/sda

This is it.

Now you can reboot your system, and enjoy using your previously installed Ubuntu, after un-mounting the system by:

sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

and simply reboot:

sudo reboot

---

### Post by bcbc on 2010-11-21
> **oboedad55 said:**
> Lilo? I have to respectfully disagree with this...

Probably you didn't see Cazzer's other thread - but ubuntu was installed with Wubi. Wubi boots via windows, and windows requires the windows boot loader. 

If you don't have a windows disk, lilo does the same job (I know, I am using it right now).

---

### Post by bcbc on 2010-11-21
Cazzer - a bit of background... since 10.04 grub has been breaking wubi installs. They released a fix, but it only works on wubi installs on the same partition as windows. Since you installed on D: you are still affected.

Whenever you update grub it prompts you where to install the bootloader. But the message is confusing. You likely saw a screen offering /dev/loop0 and /dev/sda. Choosing the first does nothing, choosing the second causes grub to install itself to the drive MBR - preventing Windows (or wubi ubuntu from booting).

To avoid this, you should leave both options unchecked, and proceed to the next screen, confirm that you 'don't want to install grub' and proceed. (This is the confusing part, since you do want to install grub - just not the bootloader part).

It's frustrating but the grub developers can't figure this problem out in situations like yours (since April this year), and now they've released a new update that will again prompt users to do what you did.

---

### Post by oboedad55 on 2010-11-21
> **bcbc said:**
> Probably you didn't see Cazzer's other thread - but ubuntu was installed with Wubi. Wubi boots via windows, and windows requires the windows boot loader. 

If you don't have a windows disk, lilo does the same job (I know, I am using it right now).

You are correct, I did not see his other post. This serves to remind me why, at most, I dual boot and not allow Windows to be part of the Linux equation. Thanks for the correction, it's obviously an important point.

---

