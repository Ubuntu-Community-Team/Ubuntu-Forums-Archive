---
title: "Grub issue - dual boot XP"
date: 2010-05-12
forum: General Help
---

### Post by wardrich on 2010-05-12
Hey,

I'm trying to Dual-boot my system with Ubuntu and XP.  I've done it lots in the past with little-to-no problems... but this time it's just not working.  I think part of the issue may be in the partitions on my main HDD...

Not sure the best way to explain it, but here's what Palimpsest says:

> 
**94 GB Filesystem**
94GB/88GiB
NTFS FIle System
Partition 1 (HPFS/NTFS(0x01))
/dev/sdb1

**66 GB Extended**
66GB/61GiB
Unrecognized
Partition 2 (Extended(0x05))
/dev/sdb2

**2.7 GB Swap Space**
2.7GB/2.5GiB
Swap Space
Partition 5 (Linux Swap(0x82))
/dev/sdb5

**63 GB Filesystem**
63GB/59GiB
Linux Ext4 (Version 1.0) File System
Partition 6 (Linux (0x83))
/dev/sdb6/ mounted as [COLOR="Blue"]/[/COLOR]


And here's the windows XP bit from my grub.cfg:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f6d4ad56d4ad1a3f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

I think maybe I just need to change the (hd1,1) or the (hd0) bit to something, and I've tried a few different combinations (all of which have failed) so I'm starting to run out of ideas.  When I boot that XP option, it flashes an error on the screen, but it goes by so fast I have no idea what it says, then it goes back to loading GRUB again.

Any help or ideas would be great... I'd really like to get some new songs on my iPod touch... lol.

--Richard

---

### Post by Zintha on 2010-05-12
I read this after opening it and realising i'm late! But google "fixboot" and see if that might be a solution.

I had a similar situation!
I'll be back in... a while to check any progress!

---

### Post by bumanie on 2010-05-12
I think windows should be (hd0,1) under the new grub 2 labelling system. However what you are describing has been a common issue after a 10.04 installation/upgrade - [look here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") and see if this may help you - it has been a common fix for problems such as yours. I would try this before playing around with /boot/grub.cfg, but carefully read the instructions first. Hope it helps.

---

### Post by wardrich on 2010-05-12
Thanks for the help guys, I'll look into this.

> **Zintha said:**
> I read this after opening it and realising i'm late! But google "fixboot" and see if that might be a solution.

I had a similar situation!
I'll be back in... a while to check any progress!

Sorry Zinthia, I posted it then went to bed, I hope you didn't spend too much time checking this post for progress.  Thanks for your help, though.  I'll post my results when the time comes.

---

### Post by bumanie on 2010-05-12
You can do fixboot and fixmbr from an xp installation cd, but that will over-write grub and then you would have to reinstall grub from a live ubuntu cd - take a look at the other page first and see if it may suit/sort out your problem.

---

### Post by wardrich on 2010-05-12
Okay, so I just ran Testdisk and so far did all but the last step of the wiki... and as it stands, It looks like ntldr is loading instead of grub, and I can get into XP, but now my ubu partition isn't booting properly.  lol.  I'm using the liveCD right now, and I'm going to try running that last step on the testdisk wiki and hopefully all will be well.

---

### Post by oldfred on 2010-05-12
If you also ran  fixMBR from the windows repair and not just the testdisk, then you may have to reinstall grub. But you showed windows in sdb1, so you have sda? Is windows boot in sdb and grub in sda and you change boot order in BIOS to get grub to boot?

To see entire configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

