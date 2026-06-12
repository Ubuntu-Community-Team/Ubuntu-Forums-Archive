---
title: "Dual booting with multiple windows"
date: 2009-10-19
forum: General Help
---

### Post by turgidtoupee on 2009-10-19
I currently have ubuntu installed alongside windows xp and windows 7. When I boot currently it gives me the grub menu with ubuntu and all the ubuntu options and at the bottom Windows Vista (loader) which takes me to the vista/7 boot loader, which then gives me the option of XP or Vista.
I was wondering if there was a way to skip the vista/7 bootloader and have separate entries for windows 7 and xp.

---

### Post by Giblet5 on 2009-10-19
Of course.

You have to understand a little about disk partitions, but it's pretty easy.

My Grub menu lets me boot Jaunty-32, Karmic-64, Win7-64, XP-32, Vista64, CentOS5-64, and Solaris. Directly.

Hint: If you label your partitions, it makes it a LOT easier.

---

### Post by turgidtoupee on 2009-10-19
So how would I do that?

---

### Post by Giblet5 on 2009-10-19
> **turgidtoupee said:**
> So how would I do that?

I recommend that you do it correctly. :)

Whatcha got? Post the output of ```
sudo fdisk -l
``` and identify the XP and Win7 partitions for me.

---

### Post by Giblet5 on 2009-10-19
OK, maybe someone else can use the info.

```
sudo fdisk -l
``` will output available disks, and their partitions, in a specific order.

The first disk will be hd0, the second will be hd1, and so on.

The first partition of the first disk is hd0,0 and so on.

This mapping is mirrored in /boot/grub/device.map but that file can be wrong, so I recommend doing this with the fdisk command above.

Our example mapping:
(hd0)  /dev/sda
(hd1)  /dev/sdb

So, let's say we have a Win7 partition on the first partition of the first disk. That would be hd0,0 so we'd have a grub entry like this: ```
default saved
timeout 60
color white/blue blink-black/light-gray

title Windows 7 64bit
root (hd0,0)
chainloader +1
savedefault
makeactive
```

Note that I put that puppy at the top of menu.lst: it doesn't get overwritten by update-grub that way.

Now, let's say I have an XP partition on the first partition of the second drive. That'd be hd1,0 so the two entries look like ```
default saved
timeout 60
color white/blue blink-black/light-gray

title Windows 7 64bit
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows XP Pro 32bit
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1
savedefault
makeactive
```

Tweak the file, save it, then do ```
sudo install-grub /dev/sda
``` assuming your hd0 equates to /dev/sda...

It's really simple once you read the docs.

And it all gets changed in Karmic.

---

### Post by louieb on 2009-10-19
Maybe - maybe not. Depends on how you installed the the 2nd Microsoft OS. From what you described probably not. The MS installer has a weird way of setting up multi-booting when it finds another Microsoft OS on the same hdd.  

Some technical details here:    [Multibooters, Pictures here worh 1000+ words]("http://www.multibooters.co.uk/multiboot.html")

To know for sure follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by Giblet5 on 2009-10-19
> **louieb said:**
> Maybe - maybe not. Depends on how you installed the the 2nd Microsoft OS. From what you described probably not. The MS installer has a weird way of setting up multi-booting when it finds another Microsoft OS on the same hdd.  

Some technical details here:    [Multibooters, Pictures here worh 1000+ words]("http://www.multibooters.co.uk/multiboot.html")

To know for sure follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

+1

In related news: grub2 breaks everything but can (usually) do it all automatically.

---

### Post by turgidtoupee on 2009-10-19
Thanks for the reply. I tried what you said, but when trying to boot into windows 7 I am given the error BootMGR not found. Press Ctrl+Alt+Del to restart. However when booting XP I am given the bootloader, as before when choosing Windows Vista(loader). I think the problem is that I need to somehow get round the bootloader for windows, but have no idea how.

---

### Post by rocktofakie3 on 2009-10-19
Can someone click out my post cause i really need help

> [http://ubuntuforums.org/showthread.php?p=8111747#post8111747](http://ubuntuforums.org/showthread.php?p=8111747#post8111747)

---

### Post by Giblet5 on 2009-10-19
> **turgidtoupee said:**
> Thanks for the reply. I tried what you said, but when trying to boot into windows 7 I am given the error BootMGR not found. Press Ctrl+Alt+Del to restart. However when booting XP I am given the bootloader, as before when choosing Windows Vista(loader). I think the problem is that I need to somehow get round the bootloader for windows, but have no idea how.

Can you post what you have now?

---

### Post by Giblet5 on 2009-10-19
> **rocktofakie3 said:**
> Can someone click out my post cause i really need help

That's a great big fat NO Mister Line Jumper Guy. Didn't your parents teach you manners? Were you raised by wild hogs?

---

### Post by turgidtoupee on 2009-10-19
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee4bee4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58175   467290656    7  HPFS/NTFS
/dev/sda2           58176       60801    21093345    5  Extended
/dev/sda5           58176       60686    20169576   83  Linux
/dev/sda6           60687       60801      923706   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbc4cbc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf83ef83e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24321   195358401    7  HPFS/NTFS

And booting:

(Linux ones)

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root	(hd0,0)
savedefault
makeactive
chainloader	+1

title Windows 7
map (hd0) (hd2)
map (hd2) (hd0)
root (hd2,0)
chainloader +1
savedefault
makeactive

---

### Post by Giblet5 on 2009-10-19
> **turgidtoupee said:**
> title Windows 7
map (hd0) (hd2)
map (hd2) (hd0)
root (hd2,0)
chainloader +1
savedefault
makeactive

Try removing the map lines, then doing ```
sudo install-grub /dev/sda
```

As **louieb** pointed out, newer Windows releases can do odd things if they see another Windows install and it may have handled the drive mapping itself.

As for Windows multiboot menu, you should be able to fix that via C:\boot.ini tweaks.

---

### Post by turgidtoupee on 2009-10-19
I shall have to look into changing my boot.ini to get rid of the boot manager then. Thanks for your help.

---

### Post by louieb on 2009-10-20
> I shall have to look into changing my boot.ini to get rid of the boot manager then.

Don't do that. You may need it. Please run and post the output of the script. 
It will tell us a lot about what you can and can't do.

---

### Post by Giblet5 on 2009-10-20
> **louieb said:**
> Don't do that. You may need it. Please run and post the output of the script. 
It will tell us a lot about what you can and can't do.

That's a really good idea. Having run into this a time or twenty, I have learned that if mapping the drive order causes a Windows error, removing that mapping fixes it.

Your way uses science. Mine uses trial and error.

Science is better...

---

### Post by louieb on 2009-10-20
> **Giblet5 said:**
> Your way uses science. Mine uses trial and error.

Thomas Edison used trial and error when inventing the light bulb. He found 10,000 ways that did not work before he found 1 that worked like he wanted. 

:guitar:The script is not prefect. The info in it makes it easier - not science - but an educated guess.

---

