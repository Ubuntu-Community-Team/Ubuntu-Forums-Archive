---
title: "Software Raid - Both Drives - Both With Root?"
date: 2011-05-19
forum: General Help
---

### Post by Roasted on 2011-05-19
Let's say I have a box with two 500gb drives. Is it possible to partition it like 10gb root/490gb data and have BOTH partitions RAID1 each other?

SDA
10gb root
490gb data

SDB
10gb root
490gb data


All done through software RAID with a mirror?

I tried to do it just now in the alternate installer but it hit me with an error. So I popped in a flash drive and installed the OS on it (of course, with no swap, since swap would kill a flash drive's read/write life) and used the 500's in RAID1.

Anyway, is the above possible? Or would that require a hardware controller?

---

### Post by Roasted on 2011-05-21
Any idea?

---

### Post by tgalati4 on 2011-05-21
You could, but it's better to simply have the large partition in RAID and leave two small boot partitions intact.  You can rsync them once a month if you really need to mirror them.  Also, you would want 30 GB boot partitions.  If you ever decide to recompile your kernel or build applications, you will need some space for the build environment.

Leaving the small partitions as non-RAID makes it easier to troubleshoot and use recovery utilities should things go bad.

---

### Post by Roasted on 2011-05-21
> **tgalati4 said:**
> You could, but it's better to simply have the large partition in RAID and leave two small boot partitions intact.  You can rsync them once a month if you really need to mirror them.  Also, you would want 30 GB boot partitions.  If you ever decide to recompile your kernel or build applications, you will need some space for the build environment.

Leaving the small partitions as non-RAID makes it easier to troubleshoot and use recovery utilities should things go bad.

I have installed every application known to man and I still have yet for my root partition (also containing /boot) to take up more than 12gb. What would I need 30gb for???

Edit - Okay. I'm having some issues with software raid here. I hope somebody can help.

I found this guide : [http://www.linuxlog.org/?p=144](http://www.linuxlog.org/?p=144) and it said there are some steps about creating an MD device and which type of raid I wanted to use.

I used Ubuntu 11.04 64 bit alternate installer CD. I went through these steps. I created new partition tables. I selected software raid on each drive. But it never asked me to create an MD device and it never asked me which type of raid I wanted to use.

After I went through the installer process, there was no fstab entry for my raid'ed drive. There was nothing, as if the raid array wasn't fully set up. Frustrated, I did some googling, and I came across that guide and realized I was never asked about anything of the array, so how could Ubuntu know to mount /dev/md0 to /media/storage or whichever location I wanted?

What did I do wrong? Can anybody link me to a very thorough software raid guide? And NOT Ubuntu's, as that has less screenshots and direction than the link I posted above.

---

### Post by Roasted on 2011-05-23
So, did I do something wrong? I just don't understand where those additional menus were I never got to. :(

EDIT - yeah. I suck. Like no. really. I'm an idiot. Once you select the drives to be software raid you need to select this magical step at the top of the partitioner screen. I guess I assumed anything I needed to further configure would be located at the bottom. My mistake.

```
Do the same thing for the rest of disks in the RAID then select &#8220;Configure software RAID&#8221;
```

Oops...

---

