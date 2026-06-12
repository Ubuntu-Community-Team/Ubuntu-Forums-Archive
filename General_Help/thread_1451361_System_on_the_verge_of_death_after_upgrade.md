---
title: "System on the verge of death after upgrade"
date: 2010-04-10
forum: General Help
---

### Post by Eagleguy125 on 2010-04-10
My system is all but completely dead so far as I can tell. I was dual-booting Ubuntu 9.10 and W7 Pro, but I decided to try 10.04 beta 2 out since I usually at least beta test software that I like. A number of things went horribly wrong in that installation, but none of that became apparent until I rebooted into 10.04.

After the installation, I could no longer boot into Windows (instead of the bootloader for Windows, I get a black screen and a flashing line at a terminal that I can't type into. The only input that affects the system whatsoever is Ctrl+Alt+Del.) In addition, 10.04 was really, really broken. I finally got parts of it fixed, but it was too unstable for me to really use, so I just bit the bullet and reinstalled 9.10.

Again, though, something went horribly wrong, and although it booted correctly twice (not really sure how that happened, actually.) I can now not boot into either operating system. In fact, I don't even get to the grub menu in which I could select which OS I wanted to use--my system now boots, after around fifteen seconds with the screen off and the CPU fan running hard, directly to a grub terminal without actually giving me access to anything on the system. It's like grub decided to randomly install itself into some isolated portion of my disk.

So, here I am, booting from a 9.10 LiveCD. If anyone has anything like a suggestion or comment, please drop a reply. I'm a computer science major and really, really need my desktop to be working for school. (I know, I know, I should be able to fix this because I'm a comp sci. Go ahead and laugh. I can appreciate the irony, too.)

Thank you.
--Ethan

---

### Post by motsteve on 2010-04-10
I don't laugh at ANYONE with this problem.  Since there is no SuperGrub disk for grub2 that I know of, try reinstalling grub2 on your Karmic partition with the liveCD's terminal.  You have to mount the linux partition and then chroot into it to do your thing.  It's quite involved so you may need the following to aid you:


[http://ubuntuforums.org/showthread.php?t=1295297](http://ubuntuforums.org/showthread.php?t=1295297)

Good luck.

---

### Post by Eagleguy125 on 2010-04-10
> **motsteve said:**
> I don't laugh at ANYONE with this problem.  Since there is no SuperGrub disk for grub2 that I know of, try reinstalling grub2 on your Karmic partition with the liveCD's terminal.  You have to mount the linux partition and then chroot into it to do your thing.  It's quite involved so you may need the following to aid you:


[http://ubuntuforums.org/showthread.php?t=1295297](http://ubuntuforums.org/showthread.php?t=1295297)

Good luck.

Thanks. Trying that now.

---

### Post by Eagleguy125 on 2010-04-10
Well, I tried all of that and the commands executed without issue... But it still booted to a grub terminal that didn't have access to anything of consequence. With that in mind, I reinstalled 9.10 (it's not like I had any new data anyway.) and it booted properly to a grub menu. However, booting to windows still won't work.

---

### Post by motsteve on 2010-04-10
> **Eagleguy125 said:**
> Well, I tried all of that and the commands However, booting to windows still won't work.

One thing that will sound odd, but is true is that Windoz has to be on the first drive and the first partition to be recognized.  If you do a:

$ sudo fdisk -l 

and it shows that the Windoz partition is there, but in the wrong place, you may consider relocating it to the right place using clonezilla to copy it to a safe place and then clean the first drive and recopy it to the first partition and then install 9.10 along side Windows in the remaining space on the drive.  What a long sentence! :)

Here's what mine looks like:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4943    39704616    7  HPFS/NTFS

Also, when you do a update-grub you should see Windoz go into the grub.cfg file as it is working its magic.
/dev/sda2            4944        9729    38443545    5  Extended
/dev/sda5            4944        9486    36491616   83  Linux
/dev/sda6            9487        9729     1951866   82  Linux swap / Solaris

---

### Post by Eagleguy125 on 2010-04-10
See, I've actually got Windows on its own physical disk taking up the entire drive, and then a twin hard drive (not linked in any way, but identical hardware) partitioned into some amount close to 80GB for data, 100GB for Ubuntu, and some space for swap and such. If I instruct the BIOS to boot from the first hard drive I get nothing, and if I tell it to work from the second drive I (now, since reinstalling 9.10) get the proper grub menu.

For reference, here's my sudo fdisk -l output:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03390339

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24322   195358560+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007481e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11268    90505216    7  HPFS/NTFS
/dev/sdb2           11269       24321   104848222+   5  Extended
/dev/sdb5           11269       24207   103932486   83  Linux
/dev/sdb6           24208       24321      915673+  82  Linux swap / Solaris

```

---

