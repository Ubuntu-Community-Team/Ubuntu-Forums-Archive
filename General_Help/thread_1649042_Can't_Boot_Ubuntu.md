---
title: "Can't Boot Ubuntu"
date: 2010-12-19
forum: General Help
---

### Post by gamebittk on 2010-12-19
My Ubuntu installation crapped out today. :/ 

I installed Ubuntu a couple of months ago using the Wubi installer. Everything was working great, until today. Today, I went to restart my PC, but soon after hitting 'Restart' the computer became unresponsive. I couldn't get any keyboard/mouse input to register on screen, so I did a force shut down by holding down the power button. When I turned the computer back on, I selected Ubuntu from the boot menu. The computer printed some messages that passed by relatively quickly so I'm not sure exactly what they said, but it was something along the lines of "NTFS3: wubibuilder failed to load", and then it went straight back to the boot menu. Tried again and again with no success, so I loaded my Windows 7 install to investigate from there. I found a link to Explore2fs on these forums, so I loaded it up, but it apparently can't locate my Ubuntu partition, or at least I don't see my files. I ran the Wubi installer again to see what it would say, and it tells me that a previous installation was detected, and gives me the option to uninstall. Does anyone have an idea of what went wrong, or know how to fix this? I'd really appreciate the help! 

**TLDR;** Ubuntu not booting up, partition may be lost, please help me fix it.

---

### Post by PhantmKllr on 2010-12-19
WUBI installations are tricky things. The problem is, that when it craps out, there's pretty much nothing you can do about it.

If there's information on your WUBI Ubuntu installation that you need off, then here's how (if possible). The "partition", that Ubuntu is installed in by WUBI, is in reality a disk image, possibly SquashFS. So open Windows Explorer, then open the Ubunt installation folder (probably under Program Files). Then look for the Ubuntu disk image. If the file is SquashFS, then you can use this software (at your own risk):

[http://fragilematter.blogspot.com/2010/02/squashfs-tools-40-windows-binaries.html]("http://fragilematter.blogspot.com/2010/02/squashfs-tools-40-windows-binaries.html")

If the file isn't SquashFS, then just download PeaZip:

[http://www.peazip.org/]("http://www.peazip.org/")

Open the disk image, then extract the files you need.

Hope that helps! :D

---

### Post by bcbc on 2010-12-19
Look at the Wubi Megathread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

There is a link to ext2read that can read the ext4 formatted virtual disk. There's also a link to the bootinfoscript there and I suggest you run it and post the results before trying exotic uncertain fixes.

---

### Post by PhantmKllr on 2010-12-19
> **bcbc said:**
> Look at the Wubi Megathread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

There is a link to ext2read that can read the ext4 formatted virtual disk. There's also a link to the bootinfoscript there and I suggest you run it and post the results before trying exotic uncertain fixes.

Yup, that's the way to go. Thanks Bcbc, I don't know much about WUBI. :)

---

### Post by gamebittk on 2010-12-21
Thanks for your responses PhantmKllr and bcbc. 

Until now I was under the impression that Wubi installs were just as good as standard installs. I'm probably going to install Ubuntu the standard way now that I know that isn't the case. 

Until then, I'd like to repair my current install. 

I ran the boot info script as bcbc suggested. Here's the problem part: 

```
sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```The WUBI Megathread mentioned that in some cases, GRUB updates might case issues. But from what I understand there are no updates that would affect Ubuntu 10.10, however before restarting my PC, I did install updates via the Package Manager. Is it possible that a GRUB update was installed that caused this issue? Is this even the kind of problem GRUB would cause? 

Ok, so my problem is failure to mount the filesytem. I'd imagine it's a bit different to repair with a Wubi install since like PhantmKillr and bcbc mentioned, the 'partition' is actually a disk image.  How would I go about fixing this?

---

### Post by bcbc on 2010-12-21
If you're sure that you have 10.10 then yes there have been no grub updates that I am aware of. But note if you installed wubi from the ubuntu.com site, then it's still set at release 10.04(.1). 

So... bootinfoscript failed to mount the root.disk. This can mean that the root.disk has been corrupted, but this isn't always the case. However, since you did a forced shutdown - it's definitely a possibility.

Since you haven't included the entire bootinfoscript, I can't tell whether you installed wubi on the same drive as Windows (C: ) - which is another useful indicator as to whether it was a grub update that broke it. 

What I'd do is try to loop mount the root.disk from your live CD. If that fails, you can try to 'fsck' the root.disk (only do this if it's not mounted).
```
sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
Only if you failed to mount the root.disk, then you can try:
```
sudo fsck /media/win/ubuntu/disks/root.disk
```

Post back when you have more info and consider posting the full bootinfoscript results.

---

