---
title: "Grub can't find partition at boottime"
date: 2010-09-14
forum: General Help
---

### Post by n0c0d3 on 2010-09-14
I had my HD partitioned with Win7 and 2 versions of Xubuntu (32 and 64  bit). and Grub as multiboot loader. I removed the 32 bit version and  assigned the free space to the 64 bit version using the Gparted bootCD,  but now Grub can't find any partition anymore at boottime. All I get is  this message and prompt when I try to boot my computer:

error: no such partition
grub rescue>

My  Linux partition is supposed to be sda6. When using the 'ls' command I  get quite few entries, from which one is (hd0,6), which is sda6 I  suppose.
I can list the contents of directories on (hd0,6).

I've tried instrucions from [this page]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode"), but many commands don't work, like 'linux', 'initrd' and 'boot'. When I use the 'set' command I get:

prefix=(hd0,7)/boot/grub
root=(hd0,7)

But when I use 'ls (hd0,7)/boot/grub' I get 'no such partition'.

I'm  totally lost from here. I really don't want to loose my current OS's.  Is there a way to recover fom this so I get the Grub boot menu with my Win7 and Xubuntu entries again?


Any help is highly appreciated!

Bart

---

### Post by philinux on 2010-09-14
I would set up a chroot from the livecd and just run update-grub first.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by drs305 on 2010-09-14
It sounds like Grub2 is incorrectly pointing to the wrong partition if your install is on sda6. At the G2 prompt, enter these commands:
```

set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
linux /vmlinuz root=/dev/sda6 ro
initrd /initrd.img 
boot

```

You should be able to do a bit of investigating to see if the commands will work. After you run the first two, type:
```
ls (hd0,6)/
```
Does it show "vmlinuz" and "initrd" ?
```
ls (hd0,6)/boot
```
Does it show your kernels and initrd images?

If the answer to the first question is no and the second yes, change the last two commands to the following:
```

linux (hd0,6)/vmlinuz<tabtocomplete> root=/dev/sda6 ro
initrd /init<tabtocomplete> 
boot

```

If you still can't boot, run *meierfera's* [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/") and post the results.

---

### Post by parleg on 2010-09-14
I am assuming you are using the latest version of Ubuntu which has grub2.
If I were you, I would try the following:

1) Boot using the live CD of Ubuntu 10.04
2) fdisk -l /dev/sdX (where X is any of a,b,c,d ) and identify your / and /boot partitions (if you have a seperate /boot) Lets assume /dev/sda1 is your / and you are not using a seperate /boot partition
3) mkdir /mnt/sda1
4) mount /dev/sda1 /mnt/sda1
5) mount -t proc none /mnt/sda1/proc
6) mount -o bind /dev /mnt/sda1/dev
7) chroot /mnt/sda1 /bin/bash
== the following are commands in chroot environment ==
 8) grub-install --root-directory=/ /dev/sda   # this will install grub on /dev/sda
9) update-grub2 # this will rescan your available kernels and build your grub.cfg
10) exit # exit out  of chroot
11) umount /dev/sda1/proc
12) umount /dev/sda1/dev
13) umount /dev/sda1
14) reboot into your environment

Steps 2 to 7 are done for you if you choose the rescue a broken system option and use chroot option appropriately.

Summary - You are reinstalling grub2 and reconfiguring grub2 menu based on your environment.
I use this when I am doing a reinstall (I backup / when booted from the live CD) This way I do not need to download all the updates,

Hope this works.

---

### Post by n0c0d3 on 2010-09-14
I'm back!
I used the blog solution philinux linked to and it worked like a charm. All the former Grub entries were back and I could boot them instantly, except for the Xubuntu 32 bit of course. Also Win7 booted without a problem (had a lot of updating to do as I hadn't booted in Windows for several weeks ):P).
Now all I have to do is remove the Xubuntu 32 bit entries from the Grub menu, but (I think) I know how to do that.

<==== Btw, the version of Linux I use is visible here.

Thanks for your quick help guys!
Bart

---

