---
title: "Grub with 2 Ubuntu"
date: 2010-08-26
forum: General Help
---

### Post by Shinka.S on 2010-08-26
I have two hard drives, the first has Ubuntu 10.04, and I want to install another 10.04 on the other drive (this one would stay at 10.04 while the other will be my "bleeding" edge Ubuntu).

I noticed that, with time, The Grub menu added new options, probably Kernel revisions. When I'll have my 2 Ubuntu on different hard drives, will GRUB; 

(1) Automatically detect new kernel revisions for both Ubuntu ?

(2) Only update options for one Ubuntu, but I can easily update all options with "update-grub" ?

(3) Only update one Ubuntu, and I'll have to do complicated stuff to update the options for the other Ubuntu ?

(4) Rebel and try to take over humanity ?

---

### Post by garvinrick4 on 2010-08-26
They are new Linux Kernels and you will get a lot of them. Leave about two in each version installed and take the older ones out in Synaptic. Just type in Synaptic 2.6.35-14 or whatever Linux kernel it is you want to remove and remove the headers 2 of them and 1 kernel. It will just be part of maintaining your Linux systems.

---

### Post by Shinka.S on 2010-08-26
Thanks, but I don't want to know how to remove them, I want to know if I'll see new options for the kernels for both Ubuntu in the grub menu.

---

### Post by garvinrick4 on 2010-08-26
> **Shinka.S said:**
> Thanks, but I don't want to know how to remove them, I want to know if I'll see new options for the kernels for both Ubuntu in the grub menu.
Yes

---

### Post by oldfred on 2010-08-26
Which ever Ubuntu you boot will automatically get updated. If you update the other install you will have to run sudo update-grub in the boot install to update.

But you can add to 40_custom a boot stanza that will always boot the most current kernel.

From Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

You can customize your grub menus:
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

A Very Easy Alternate GUI Method - Ubuntu-Tweak
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by -kg- on 2010-08-26
> **Shinka.S said:**
> Thanks, but I don't want to know how to remove them, I want to know if I'll see new options for the kernels for both Ubuntu in the grub menu.

> **garvinrick4 said:**
> Yes

After you run "sudo update-grub" in the terminal of the installation that installed GRUB bootloader in the MBR.  You would have to do that every time you have a kernel update in the other installation.  The "controlling" installation will update this automatically.

Now if you're interested in experimentation, you can also go oldfred's way.  I would have to study it a bit to understand what he was explaining, but it would save you having to run "update-grub" every time you had a kernel update.

---

### Post by Shinka.S on 2010-08-28
Great, I have my answer, thanks !

---

