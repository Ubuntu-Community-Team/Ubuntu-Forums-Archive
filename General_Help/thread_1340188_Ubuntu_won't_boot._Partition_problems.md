---
title: "Ubuntu won't boot. Partition problems"
date: 2009-11-28
forum: General Help
---

### Post by shiny123 on 2009-11-28
Hey all, I'd really appreciate some help

I have a laptop with windows vista on it and I installed ubuntu 9.10 with no problems. My harddrive was partitioned, if i remember correctly, into roughly 30 mb for FAT, 80 gb for windows vista, 14 gb for a random partition entitled "recovery disk" for windows vista, 10 gb for /, 40 gb for /home, 2 gb for /swap, and a 5 or 10 gb spare partition called /ext2spare (which i never ended up using). After some time, I wanted to install windows 7. After many attempts, i found out the original file i had downloaded (legally) wasn't perfect, so i redownloaded, and installed 7 onto the recovery partition, after formatting it. I then discovered that windows had replaced GRUB2, and so I couldn't get onto ubuntu. So after much searching, i tried a few methods, and one of them must have worked, because when i rebooted, i found GRUB2 back. I can boot from GRUB2 into the windows bootloader into windows 7 without problems (and vista also probably still works by the same method). However ubuntu doesn't work.

Here's what happens: I start the laptop. GRUB loads. I press enter for "Ubuntu, Linux 2.6.31-14-generic ". The white ubuntu logo appears, after a bit it disappears and goes into that visible terminal mode (or whatever it's actually called). It says:

fsck from util-linux-ng 2.16
/dev/sda5: clean, 146420/610800 files, 791890/2441880 blocks
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/ext2spare: waiting for UUID=95E026AD-3ec7-4d9a-847b-e.....
/home: waiting for UUID=.......
swap: waiting for UUID=.......
 * Starting init crypto disks    [OK]

(I didn't bother typing the UUIDs.)

Worried about my files on /home, I booted from a live ubuntu CD. I opened up Disk Utility to see if my beloved /home was still there. I see this:
1) 160 GB Hard Disk
    2) DellUtility 41 MB FAT
    2) windowseven 15GB NTFS
    2) OS 95 GB NTFS
    2) 49 GB Extended Contains logical partitions
        3) 10 GB Filesystem Linux Ext4 (version 1.0)
        3) 39 GB Free unallocated Space

I also ran "sudo fdisk -l" which gives the devices: sda1 Dell Utility, sda2 NTFS, sda3 NTFS, sda4 Extended, sda5 Linux.
I don't understand what's going on. I just want my files from /home.

I don't understand how this happened. Ubuntu was working fine when I last booted into it. I only formatted (on windows) the "recovery" partition and only attempted to install windows 7 into that partition. If it helps, I am using ext4 and I chose the encryption option for /home. If it helps, I've also attached the results.txt of the boot info script.
By the way, I'm a quite a noob, so I apologise in advance. Sorry for the lengthy message.

---

### Post by john newbuntu on 2009-11-29
Boot using your liveCD and open a terminal.  Then type:
```
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
```
reboot and cross fingers.

---

### Post by trzarocks on 2009-12-01
> **john newbuntu said:**
> Boot using your liveCD and open a terminal.  Then type:
```
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
```reboot and cross fingers.

This was enough to get me to a fix, but I couldn't mount sda5.  So I ended up with:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
```

Rebooted and saw the GRUB loader, which I didn't have before.  After selecting the only kernel option, I was able to log in to my notebook.

Thanks!  :D

---

### Post by shiny123 on 2009-12-02
> **john newbuntu said:**
> Boot using your liveCD and open a terminal.  Then type:
```
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
```reboot and cross fingers.

Hey, thanks for trying to help.
I tried the suggestions, and this is what happened:

> 
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/boot
mount: mount point /mnt/boot does not exist
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/boot
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
It broke GRUB. I fixed that.
Ubuntu still doesn't work. When I boot into it, it just says:
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/ext2spare: waiting for UUID=95E026AD-3ec7-4d9a-847b-e.....
/home: waiting for UUID=.......
swap: waiting for UUID=.......
 
Does that mean it's like these three partitions have ceased to exist? Sigh, I suppose I'll have to accept my files are gone. Would be nice to know how it happened though...

---

### Post by jeschvi on 2009-12-02
You may have to edit /etc/fstab. The first field is the "block special device". If you have it on the form UUID=.... , then the id may be wrong? You may be able to find it using the command blkid - but since you boot from a live CD, I don't know if that would work. 
Alternatively, I would try replacing the UUID=.... stuff with something of the form /dev/sdb7. Then you just need to figure out what the device names are. In my fstab this was actually written in a comment.

---

### Post by oldfred on 2009-12-02
If the fstab is the one you posted in results.txt you do not have /home swap and the "spare" partition. It is looking for UUID's that blkid and fdisk partitions show do not exist anymore. You should add swap back, did you delete your /home? And I assume the spare does not matter. If in your fstab you delete the entries for /home, swap & the spare you should be able to boot & it will create a new home inside your root. You still should create /swap unless you have over 4GB of memory and never run any large applications or hibernate and even then you should still have swap.

---

### Post by winh8r on 2009-12-02
Hi 
Shiny123, before you go and change everything ,you can save your "lost" files.
Firstly, stop using the disk that they are "lost" on as soon as possible.
Get access to the internet on someone elses computer and download a utility called PhotoRec it was designed for recovering deleted photos but will recover all sorts of other files too.
It is best to put your disk into another computer as a slave and recover to the master on the host computer(or use an external HDD)
Just select the partition you want it to recover from and leave it to run.

I have used it many times to recover JPGs and documents and have been 100% successful every time.

Christophe Grenier who wrote the program also has a utility called TestDisk which will allow you to fix problems on a mis-configured disk without damaging anything.

Good Luck!!

---

