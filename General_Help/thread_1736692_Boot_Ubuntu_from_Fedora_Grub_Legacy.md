---
title: "Boot Ubuntu from Fedora Grub Legacy?"
date: 2011-04-22
forum: General Help
---

### Post by ManualSparrow on 2011-04-22
I have a similar problem.

Over the past few months I installed these operating systems in this order:
Windows7 
Ubuntu 10.10 --> Xubuntu 10.10 (no seperate parition, just Synaptic'd it)
Jolicloud (JoliOS)

After Jolicloud updated to 1.2 it stopped supported various aspects of my hardware (sound, shutdown etc) but still remained at the top of my GRUB list even though I never used it, so I decided to remove it. I used the partition editor in Ubuntu to format the 17GB JoliOS partition to FAT. Then I went to terminal and entered sudo update-grub and everything seemed fine until I actually rebooted and got the lovely ```
grub rescue>
``` prompt.

I didn't have any live CDs around except a UNetBootin drive with the beta of Fedora 15 on it, so I went ahead and installed that on the old Jolicloud partition, sda7, and tried to put the bootloader there. Didn't work, so I borrowed a Ubuntu 10.10 live CD and tried a bunch of commands in the terminal, and eventually tried working grub rescue (not in terminal, in the actual GRUB). 

Finally I reinstalled the Fedora and put the bootloader on the MBR (selected just plain sda) which lets me boot Fedora (where I am now) and Windows, but Ubuntu is still stranded out there and I'd like to get back in.

The bootloader Fedora installed is the old Grub, 0.97. It shows Ubuntu as an option (because I told it to and slected the right partition in the GUI) and wants to run root(hd0,4) then chainloader +1. If I could get a GRUB or something onto sda5 (recognized as hd0,4 in GRUB) then it would work I think. So... any suggestions?

Sorry about the longwindedness, but I feel like the background is kind of important for this one. Hope I'm not hijacking the thread.

EDIT: 1. If I could just get the Fedora bootloader to find Ubuntu (rather than chainloading) that would be great. I tried running sudo update-grub in Fedora, but I got 'command not found.' Is there a different command to update the list in the old GRUB than GRUB2 or something?

FINAL NOTES:

OK, so the gist of my adventure here is that a) > Ubuntu rather helpfully creates the symlinks vmlinuz and initrd.img in the root of the filesystem linking to the latest kernel and initrd.img. Handy that when needing to create a grub entry in another partition. So, if you do still have a functioning GRUB of some kind (in my case, the one from Fedora, although the GRUB rescue command line *might* have worked too), you can tell it exactly how to boot to Ubuntu 
```
root (hd0,4)
kernel /vmlinuz root=/dev/sda5 ro quiet splash
initrd /initrd.img
``` (assuming everything on your HD is in the same partition scheme as mine) and then reinstall the Ubuntu GRUB on the MBR via terminal once there. 

Hope that was somewhat helpful - if not, read the rest.

---

### Post by drs305 on 2011-04-22
ManualSparrow,

Welcome to the Ubuntu Forums.

I moved your post to it's own thread for two reasons. One is that your post wasn't too related to the OP's, other than neither of you could boot. And secondly, I'm hoping this title will prove more adept at drawing a knowledgeable forumite who might have the answer.

I'd allow some time to see if you can sort it out as you wish since you have a bootable system.

But if you can't, or just want to take the plunge, you should be able to boot the Ubuntu LiveCD, chroot into your Ubuntu partition, and install or reinstall Grub2. If you have been playing with multiple distos and various versions of Grub, I don't think you would find it too difficult.

I've written a guide on using chroot to purge and reinstall Grub2, and the same procedures should work for you. It's the 'Chroot' link in my signature line.

---

### Post by ManualSparrow on 2011-04-22
Thank you. I guess I'll have a go at chrooting (going sudo grub-install on hd0,4 didn't work, it just spat me back out to the same loader).

Alternately, if anyone could help me figure out the exact commands to just boot one of my kernels tthat would also be great (most recent is vmlinuz-2.6.36-27-generic-pae if I remember correctly).

EDIT: Didn't do that - read on.

---

### Post by oldfred on 2011-04-22
I may have gotten all of this from drs305. You will have to change to your drive & partition in my example:

Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

Or:
Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by coffeecat on 2011-04-22
Coincidentally, I was in a similar situation to you just a couple of hours ago. I have Vista, Ubuntu Natty and Ubuntu Lucid on my laptop and installed the beta of Fedora 15 to a spare partition and allowed Fedora to install its legacy grub to the mbr. I knew that Fedora would only set up menu.lst entries for itself and Windows, but it was a straightforward job to edit menu.lst to include an entry for Natty so that I could boot into Natty and run grub-install and update-grub in Natty to get the (better) Ubuntu grub setup.

Boot up Fedora and post the output of:

```
cat /boot/grub/menu.lst
```Now su to root and post the output of:

```
fdisk -lu
```Indicate which is your Ubuntu root partition and I can tell you how to edit menu.lst to get you booting into Ubuntu from where you can re-install Ubuntu's grub2.

---

### Post by ManualSparrow on 2011-04-22
```
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,6)
#          kernel /boot/vmlinuz-version ro root=/dev/sda7
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,6)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.2-9.fc15.i686.PAE)
	root (hd0,6)
	kernel /boot/vmlinuz-2.6.38.2-9.fc15.i686.PAE ro root=UUID=18efae77-e752-4126-b095-39306230a105 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.38.2-9.fc15.i686.PAE.img
title Ubuntu
	rootnoverify (hd0,4)
	chainloader +1
title Windows7
	rootnoverify (hd0,0)
	chainloader +1
```

(ran in sudo, for the record)
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2b0dc8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     2459647     1228800    7  HPFS/NTFS/exFAT
/dev/sda2   *     2459648   409810655   203675504    7  HPFS/NTFS/exFAT
/dev/sda3       410818558   625141759   107161601    5  Extended
[COLOR="Red"]/dev/sda5       410818560   581295495    85238468   83  Linux[/COLOR]
/dev/sda6       616341504   625141759     4400128   82  Linux swap / Solaris
/dev/sda7       581296023   616333724    17518851   83  Linux

Partition table entries are not in disk order
```

Red = Ubuntu. sda7 is Fedora. By the way, thanks for the help with this. That (getting to Ubuntu, reinstalling Ubuntu's loader) is exactly what I've been hoping to do.

---

### Post by coffeecat on 2011-04-22
This, your Ubuntu stanza in your Fedora grub.conf/menu.lst:

> **ManualSparrow said:**
> ```

title Ubuntu
    rootnoverify (hd0,4)
    chainloader +1
```

The problem with chainloading to grub 2 is that if you try to install  grub2 to the boot sector of a partition, this usually fails, unlike with  legacy grub. A great shame as I used to find chainloading very useful for multi-booting. Anyway, Ubuntu rather helpfully creates the symlinks vmlinuz and initrd.img in the root of the filesystem linking to the latest kernel and initrd.img. Handy that when needing to create a grub entry in another partition. Replace the stanza above with this:

```
title Ubuntu
root (hd0,4)
kernel /vmlinuz root=/dev/sda5 ro quiet splash
initrd /initrd.img

```Once you've booted into Ubuntu, re-install grub2 to the mbr with

```
sudo grub-install /dev/sda
```And regenerate grub.cfg to get a Fedora entry with:

```
sudo update-grub
```

---

### Post by ManualSparrow on 2011-04-22
Excellent! I am typing from Ubuntu now, just reinstalled GRUB and will reboot in a sec.

> Anyway, Ubuntu rather helpfully creates the symlinks vmlinuz and initrd.img in the root of the filesystem linking to the latest kernel and initrd.img. Handy that when needing to create a grub entry in another partition.  Really useful, moving up to the top when I close the thread.

EDIT: Awesome, it worked (and I got a swanky colorful new bootloader out of it). Thanks for everyone's help.

---

### Post by ShiftieVI on 2011-07-17
Hello,
I believe I have a very similar problem as the OP, and I am hoping that someone can help guide me through fixing the problem (I am very new to Linux, not stupid, just new).

I installed Mint 10 a little while ago, and was enjoying that just fine, until I decided I wanted to check out Gnome 3. So I installed Fedora 15 with the hopes of dual booting both OS's. When I got done installing Fedora 15, low-and-behold, there was no trace of Mint any more. I believe that Mint is fine, it just doesn't show up on GRUB.

Here are the outputs of "cat /boot/grub/menu.lst" and "fdisk -lu" (as coffeecat asked of ManualSparrow).

cat /boot/grub/menu.lst
> [Shiftie@mBox ~]$ sudo cat /boot/grub/menu.lst
[sudo] password for Shiftie: 
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#                         all kernel and initrd paths are relative to /boot/, eg.
#                         root (hd0,2)
#                        kernel /vmlinuz-version ro root=/dev/mapper/vg_mbox-lv_root
#                         initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd0,2)/grub/splash.xpm.gz
#hiddenmenu
title Fedora (2.6.38.8-35.fc15.x86_64)
                       root (hd0,2)
                       kernel /vmlinuz-2.6.38.8-35.fc15.x86_64 ro root=/dev/mapper/vg_mbox-lv_root                      
                   rd_LVM_LV=vg_mbox/lv_root rd_LVM_LV=vg_mbox/lv_swap rd_NO_LUKS rd_NO_MD 
                   rd_NO_DM  LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
                       initrd /initramfs-2.6.38.8-35.fc15.x86_64.img
title GNU GRUB 2, (1.98)
                       kernel /grub2/core.img
title Fedora (2.6.38.8-32.fc15.x86_64)
                       root (hd0,2)
                       kernel /vmlinuz-2.6.38.8-32.fc15.x86_64 ro root=/dev/mapper/vg_mbox-lv_root  
                   rd_LVM_LV=vg_mbox/lv_root rd_LVM_LV=vg_mbox/lv_swap rd_NO_LUKS rd_NO_MD  
                   rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
                       initrd /initramfs-2.6.38.8-32.fc15.x86_64.img
title Fedora (2.6.38.6-26.rc1.fc15.x86_64)
                       root (hd0,2)
                       kernel /vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=/dev/mapper/vg_mbox-lv_root 
                   rd_LVM_LV=vg_mbox/lv_root rd_LVM_LV=vg_mbox/lv_swap rd_NO_LUKS rd_NO_MD  
                   rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
                       initrd /initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
fdisk -lu
> [Shiftie@mBox ~]$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000085ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   303357951   151677952   83  Linux
/dev/sda2       606715902   625141759     9212929    5  Extended
/dev/sda3       303357952   304381951      512000   83  Linux
/dev/sda4       304381952   606713855   151165952   8e  Linux LVM
/dev/sda5       606715904   625141759     9212928   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/vg_mbox-lv_swap: 4898 MB, 4898947072 bytes
255 heads, 63 sectors/track, 595 cylinders, total 9568256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_mbox-lv_swap doesn't contain a valid partition table

Disk /dev/mapper/vg_mbox-lv_root: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_mbox-lv_root doesn't contain a valid partition table

Disk /dev/mapper/vg_mbox-lv_home: 96.2 GB, 96200556544 bytes
255 heads, 63 sectors/track, 11695 cylinders, total 187891712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_mbox-lv_home doesn't contain a valid partition table
[Shiftie@mBox ~]$ 
I believe sda1 is Fedora and sda3 is Mint. Thank you anyone that can help me with this.

---

### Post by oldfred on 2011-07-18
Your sda1 is Mint, sda3 is the Fedora boot partition which is outside the Fedora main install in the LVM in sda4.

You can add the Ubuntu boot like posted above above except with your partition.

title Ubuntu
root (hd0,0)
kernel /vmlinuz root=/dev/sda1 ro quiet splash
initrd /initrd.img

I prefer grub2, so I would also suggest installing Ubuntu's grub2 boot loader to the MBR and use that to boot unless you like Fedora enough that you will boot it most of the time.

---

### Post by ShiftieVI on 2011-07-18
Thank you very much, it worked like a charm! This was a much simpler, and faster fix then other methods I had researched. I greatly appreciate the help.

---

### Post by kokoshmusun on 2011-07-21
I installed Fedora 15 on top of Ubuntu 11.04.  I tried to restore the Ubuntu option in the fedora grub.  It worked, but I still can't log into Ubuntu, because when I choose Ubuntu at boot, and enter my password, it refreshes the same gdm screen as if nothing happened.  In the meanwhile, there is an error about gnome power settings at the top right corner, and the gdm screen also looks different than it used to when I had everything intact.  Any thoughts?

---

### Post by oldfred on 2011-07-21
@kokoshmusun
It would be better to start your own thread. Did you have any parameters like nomodeset etc on grub line?

---

