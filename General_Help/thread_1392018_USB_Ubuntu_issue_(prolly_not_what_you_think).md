---
title: "USB Ubuntu issue (prolly not what you think)"
date: 2010-01-27
forum: General Help
---

### Post by BT1 on 2010-01-27
Okay first off let me clarify something.

1.) a LiveCD is the live desktop .iso running off a USB drive.
2.) My Ubuntu OS is installed on an 8 Gig hard drive, and is NOT a live CD. It is a "USB Hard Drive" with a full Ubuntu system installed to it just as you would install Ubuntu to your SATA or IDE hard drive. People often get the two confused in my experience.

Now, that said... I need some tips on how to make EXT4 run faster from this USB drive, ext4 being the default file system. I did the "alternate" install and turned off the timestamp, and I don't need a /swap partition or file because there's plenty of ram on the systems I use for this. What kind of options can you show me that will make Ubuntu more lightweight besides deleting unused apps/files or changing to Xubuntu?

Thanks for any assist!

---

### Post by snowpine on 2010-01-27
Running Ubuntu from a USB flash drive will always be slower than running it from an internal hard drive, due to 2 factors: slow USB transfer speed and slow flash read/write (especially write). It really has nothing to do with the ext4 filesystem. 

I have found that "micro" distros (such as Puppy or SliTaz) are the best choice for flash drives. Because they're so small, they can load entirely into ram, negating the flash drive performance issues.

---

### Post by t4thfavor on 2010-01-27
There are options, I would search the netbook forum for what exactly to change. I know that if you don't set it up correctly you will probably ruin your flash drive.

---

### Post by BT1 on 2010-01-27
> **snowpine said:**
> 1.) Running Ubuntu from a USB flash drive will always be slower than running it from an internal hard drive, due to 2 factors: slow USB transfer speed and slow flash read/write (especially write). It really has nothing to do with the ext4 filesystem. 

2.) I have found that "micro" distros (such as Puppy or SliTaz) are the best choice for flash drives. Because they're so small, they can load entirely into ram, negating the flash drive performance issues.

1.) Yeah, usually I run my thumb drives in RAID so I don't really experience the speed of a single thumb drive running solo. It's slower to say the least.

2.) Waaahhh I want Ubuntu x64 desktop /w cube in my pocket! :P

> There are options, I would search the netbook forum for what exactly to change. I know that if you don't set it up correctly you will probably ruin your flash drive.

Yeah I guess so. Haven't had any issues with my thumb drives yet, and I've been pushing them hard. I've got like a billion of them so losing a drive or two isn't an issue for right now.

I'm gonna try compiling my kernel and see if it helps. It prolly will, but it takes longer to compile on USB drives.

Thanks for your help so far.

---

