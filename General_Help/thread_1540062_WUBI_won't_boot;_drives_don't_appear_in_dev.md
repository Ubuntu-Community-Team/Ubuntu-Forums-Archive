---
title: "WUBI won't boot; drives don't appear in /dev"
date: 2010-07-27
forum: General Help
---

### Post by EdCole on 2010-07-27
I am running Ubuntu 9.10 with Windows XP, installed from the live CD via WUBI.   I believe that GRUB is 1.97~.

 Everyting was working just fine until after applying some of the upgrades in the upgrade manager; now Ubuntu will not boot.  Instead, it starts up the GRUB console with an error message saying that it can't find the kernel.

If you type **ls**, you see the following:

```

>ls
(loop0) (hd0) (hd0,1)

```(loop0) is the Ubuntu loopback drive, (hd0,1) is the Windows drive (the real hard drive) and they are intact. I am able to** set the root** to (loop0) and you can see the files. But the hard drive and the loopback drive do not appear in /dev, so you can't mount them.  To be precise, **there are no devices beginning with "sd" listed in /dev.**

I am able to boot the computer from the live CD, which automatically mounts the hard drive; from the live CD, I can mount the loopback drive thus.

```

> sudo mkdir /media/wubi
> sudo mount -o loop /media/8834C7D034C7C004/ubuntu/disks/root.disk /media/wubi

```So they are not broken.

How can I make the drives appear in /dev when booting from GRUB?

(BTW, Windows XP broke during an upgrade a month ago, and it won't boot, either.  I will try to fix that now that I have saved my files from the computer through Ubuntu.)

Thanks for any help you can give me.

Ed.

---

### Post by WorMzy on 2010-07-27
/dev, /sys and /proc are populated at boot up, at the grub stage they're supposed to be empty.
You need to set a kernel, an initrd image, and tell it to "boot".

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#SEC13](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#SEC13)

---

### Post by bcbc on 2010-07-27
A recent grub update is writing the grub bootloader to the drive MBR. With wubi, you need the windows bootloader. Reinstall from a windows repair disk (fixmbr on XP or bootrec /fixmbr on vista/7)

You can also use the lilo bootloader. From a live CD run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Edit:
sorry didn't read clearly. This probably doesn't apply to you.

It might be this instead:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by EdCole on 2010-07-27
Thank you to bcbc and WorMzy for answering my post. :-)

After reading the site that WorMzy gave me, I attempted to follow the instructions in  [the section on GNU/Linux]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#TOC17").  Here's what I did.

```

> root (loop0)
> linux vmlinuz-2.6.31-22-generic \
   root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
> initrd /boot/initrd-2.6.31-22-generic
> boot

```It printed much to the screen, but then just sat there indefinitely.  I scribbled the following information from the screen when it stopped.

```

RAMDISK:  Couldn't find valid RAM disk image starting at 0.

List of all partitions:
0800         78150744 sda driver: sd
  0801          78140128  sda1
0b00         1848575  sr0 driver: sr
No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk
Kernel panic not syncing: VFS: Unable to mount root fs on unknown block(8,1)(can't quite read my notes there)
Pid: 1, comm: swapper Tainted: G           W  2.6.31-22-generic#60-Ubuntu

Call Trace
[<c05722d1c>] ?printk+0x18/0x1c
[<c0572c607>] panic_0x43/0xe7
[<c0794d5c >] mount_block_root + 0x24f/0x272
[<c0794d5c>]  ?sys_mknod+0x27/0x30
[<c0794dd8>] mount_root+0x59/0x5f
[<c0794f2c>] prepare_namespace+0x14/0x188
[<c01e6f50>] ?sys_access+0x20/0x30
[<c0794348>] kernel_init+0xb2/0xb3
[<c0794348>] ?kernel_init+0x0/0xbe
[<c0104047>] kernel_thread_helper+0x7/0x10

```Is that the right set of commands for starting WUBI?  I had to guess that you would use the root=/dev/sda1 option, which would point it to the main NTFS partition of my hard drive.  Is that right? Where should I go from here?

Thanks.

Ed.

---

### Post by bcbc on 2010-07-27
> **EdCole said:**
> Thank you to bcbc and WorMzy for answering my post. :-)

After reading the site that WorMzy gave me, I attempted to follow the instructions in  [the section on GNU/Linux]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#TOC17").  Here's what I did.

```

> root (loop0)
> linux vmlinuz-2.6.31-22-generic \
   root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
> initrd /boot/initrd-2.6.31-22-generic
> boot

```It printed much to the screen, but then just sat there indefinitely.  I scribbled the following information from the screen when it stopped.

```

RAMDISK:  Couldn't find valid RAM disk image starting at 0.

List of all partitions:
0800         78150744 sda driver: sd
  0801          78140128  sda1
0b00         1848575  sr0 driver: sr
No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk
Kernel panic not syncing: VFS: Unable to mount root fs on unknown block(8,1)(can't quite read my notes there)
Pid: 1, comm: swapper Tainted: G           W  2.6.31-22-generic#60-Ubuntu

Call Trace
[<c05722d1c>] ?printk+0x18/0x1c
[<c0572c607>] panic_0x43/0xe7
[<c0794d5c >] mount_block_root + 0x24f/0x272
[<c0794d5c>]  ?sys_mknod+0x27/0x30
[<c0794dd8>] mount_root+0x59/0x5f
[<c0794f2c>] prepare_namespace+0x14/0x188
[<c01e6f50>] ?sys_access+0x20/0x30
[<c0794348>] kernel_init+0xb2/0xb3
[<c0794348>] ?kernel_init+0x0/0xbe
[<c0104047>] kernel_thread_helper+0x7/0x10

```Is that the right set of commands for starting WUBI?  I had to guess that you would use the root=/dev/sda1 option, which would point it to the main NTFS partition of my hard drive.  Is that right? Where should I go from here?

Thanks.

Ed.
This sounds more like the problem in that link I posted. As you can't boot windows, you will probably have to try replace the wubildr from a live cd. 


When I boot wubi from grub I do this:
```
insmod ntfs
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot

```
/vmlinuz has a link to the latest kernel - saves the typing.

But I don't think this will help - it looks like it accepted the commands you entered and then had another problem (if you typed the wrong command grub would likely have complained)

---

### Post by WorMzy on 2010-07-27
That looks about right; I trust you put > linux vmlinuz-2.6.31-22-generic \
   root=/dev/sda1 loop=/ubuntu/disks/root.disk ro all on one line, and without the "\", right? If it's complaining about your ram disk, try booting into an older kernel.

---

### Post by EdCole on 2010-07-27
I tried using the /boot/vmlinuz-2.6.31-14-generic kernel, and it booted! :D 

How do I make this permanent?  One [blogger]("http://calamari.wordpress.com/2009/12/01/fixing-a-broken-wiki-grub-after-ubuntu-updates/") suggests reinstalling the grub-pc package.  Does that make sense to everyone?

---

### Post by WorMzy on 2010-07-27
Reinstalling grub shouldn't make any difference, since it works when given the right arguments. You just need to update grub so it boots the older kernel by default. Unfortunately I can't assist you with this, since I've never used grub2, but this post may help you: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by EdCole on 2010-07-28
It's working now.

I got the computer to boot by falling back to the older version of the Linux kernel

```

> root (loop0)
> linux vmlinuz-2.6.31-14-generic \
   root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
> initrd /boot/initrd-2.6.31-14-generic
> boot

```I noticed that there was a GRUB upgrade in the updates list, so I decided to install all upgrades (over 200 megabytes worth), in the hope that my issue might be caused by the bug in GRUB 2 described [here]("http://ubuntuforums.org/showthread.php?t=1195275").

> 
**[COLOR=Red][SIZE=3]Important Note to Wubi (Windows Ubuntu) Users:[/SIZE][/COLOR] **
Grub2 updates in the spring of 2010 triggered a bug in the ntfs module  causing Wubi boot failures. The solution to this boot problem was posted  by Agostino Russo and is found in this Lucid Lynx [LaunchPad Bug Report #477169, Post 210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210"). The module causing the errors has been fixed and replacing the "wubildr" file in Windows permanently solves this problem. *meierfra* has kindly provided clear instructions on how to fix this problem at [http://sourceforge.net/apps/mediawik...lems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")
I let the updates run overnight, and tried rebooting in the morning.  Success! :D

Thanks to WorMzy and bcbc for all of your help!

Ed.

---

### Post by EdCole on 2010-07-28
By the way, I did use the backslash in the commands, to continue the line.  It "escaped" the newline character and allowed me to see what I was typing in the boot commands.

---

### Post by EdCole on 2010-10-02
"*Problema idem perduret*."  I thought I'd share the current state of this problem.  It turns out that the boot usually breaks when I do an upgrade.  I created a script to reinstall the GRUB.

```

#!/bin/bash
sudo apt-get --reinstall install grub-pc grub-common

```So, when I install an upgrade, I run this script.  If it doesn't boot, I manually boot Linux with the following:

```

root (loop0) 
linux /boot/vmlinuz-2.6.31-14-generic \
    root=/dev/sda1 loop=/ubuntu/disks/root.disk ro 
initrd /boot/initrd-2.6.31-14-generic 
boot    

```and then run the script again.  It will not boot 2.6.31-22 in any case, which is probably because of the bug mentioned above.  It's not perfect, but I can live with it (my wife, on the other hand, wants to stay with Windows because of this).

---

### Post by WorMzy on 2010-10-02
> **EdCole said:**
> (my wife, on the other hand, wants to stay with Windows because of this).

That's somewhat of a catch 22; the fact that you've installed it inside of Windows is the reason why it's happening. :P

Partition installations don't suffer from it. At least mine don't.

---

### Post by EdCole on 2010-10-02
> **WorMzy said:**
> That's somewhat of a catch 22; the fact that you've installed it inside of Windows is the reason why it's happening. :P

Partition installations don't suffer from it. At least mine don't.

Yes, indeed.  But I would probably never have messed with my working Windows computer (my only computer) to create a new partition for installing Linux, so WUBI still wins in my book.  :biggrin:

---

