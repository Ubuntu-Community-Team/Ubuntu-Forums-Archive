---
title: "Deleted my Ubuntu Partition in Windows - Can i rescue?"
date: 2010-10-29
forum: General Help
---

### Post by ugruntu on 2010-10-29
After several days and nights of tweaking my brand new ubuntu netbook on my brand new asus eee 1015, i,ve done something very stupid: i deleted my ubuntu partition in widows disk management. just pressed delete, did not format, did not create a new volume. 

then i restarted and i get the grub error

error: unknown filesystem
grub rescue > 

i restarted from USB into Ubuntu and tried rescue in GNUparted. I put in start i put in end, it tells me "searching for file systems" but then gets back to (parted). 

am i doing something wrong here? is there any (other) way i can recover my partition - would hate to go through the whole install process again!

---

### Post by coffeecat on 2010-10-29
The reason you are getting the grub error is because grub stage 2 and the grub configuration files are (were) on your Ubuntu root partition. So long as nothing has been written to the part of the HD where your Ubuntu root disk was, you should be able to recover the partition with test disk. Windows has (hopefully) merely edited the partition table, not changed anything on the partition area, so all you have to do is to get testdisk to re-edit the partition table back again.

I've not done this myself, but there are some useful links in this post:

[http://ubuntuforums.org/showpost.php?p=10001827&postcount=21](http://ubuntuforums.org/showpost.php?p=10001827&postcount=21)

Don't use photorec just yet - that's for recovering files. You need testdisk.

**Edit:** should have added. If you boot with your live USB you can install testdisk in that. Alternatively, you might be able to use Parted Magic:

[http://partedmagic.com/](http://partedmagic.com/)

If you can get that onto a bootable USB stick. Parted Magic includes testdisk.

---

### Post by ugruntu on 2010-10-29
am just trying (and failing) to install testdisk. running ubuntu from USB stick, in terminal i go: sudo apt-get install testdisk and i get:
E: could not get lock /var/lib/dpkg/lock - open (11:resource temporary unavailable)

before that i included the universe in the software sources. what am i doing wrong?

---

### Post by wilee-nilee on 2010-10-29
Do you want to recover Linux or just boot ms. Tell us your ms version as well.

---

### Post by ugruntu on 2010-10-29
i want to recover ubuntu - it is my primary OS. was running ubuntu 10.10 netbook remix and windows 7 light. i deleted the ubuntu partition by mistake in windows 7.

---

### Post by wilee-nilee on 2010-10-29
> **ugruntu said:**
> i want to recover ubuntu - it is my primary OS. was running ubuntu 10.10 netbook remix and windows 7 light. i deleted the ubuntu partition by mistake in windows 7.

Just wanted to make sure, coffeecat I'm sure can get you going, I'm not familiar with testdisk enough to help here.

---

### Post by coffeecat on 2010-10-29
> **ugruntu said:**
> am just trying (and failing) to install testdisk. running ubuntu from USB stick, in terminal i go: sudo apt-get install testdisk and i get:
E: could not get lock /var/lib/dpkg/lock - open (11:resource temporary unavailable)

before that i included the universe in the software sources. what am i doing wrong?

Sounds as though you have a package manager still open. Close Synaptic or Software Centre or Update Manager, whichever is open, and try to install testdisk with apt-get again. Or if Synaptic is still open, simply install testdisk with Synaptic.

wilee-nilee flatters me. :) I know that testdisk is what you need but once you get to the details I'm hoping the links I posted will guide you, or someone with partition table rescue will be able to help.

---

### Post by ugruntu on 2010-10-29
sudo apt-get install testdisk
reading package lists... done
building dependency tree
Reading state information... done
e: unable to locate package testdisk

---

### Post by coffeecat on 2010-10-29
You probably need to do a metapackage update first. Make sure you are connected to the internet and:

```
sudo apt-get update
sudo apt-get install testdisk
```

---

### Post by ugruntu on 2010-10-29
i also tried to install it with the software manager, it's not there. 

in case it is helpful, here is a screenshot of the disk. the 87GB partition is where windows is, the 3gb one is the swap and the 160 one is where the ubuntu partition used to be - that's the one i am trying to recover.

---

### Post by prshah on 2010-10-29
> **ugruntu said:**
> sudo apt-get install testdisk
e: unable to locate package testdisk

Don't try to install testdisk from a live CD/USB system. There are readymade live distro's available with testdisk pre-installed. Use one of them. See [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd) for  list of distributions that have testdisk pre-installed, use one of them, or near the end, there's a testdisk bootdisk.

TestDisk is the right way to go and will have everything back in a snap.

---

### Post by coffeecat on 2010-10-29
> **prshah said:**
> Don't try to install testdisk from a live CD/USB system.

Is there a reason for this? I once installed testdisk in a live CD session to run photorec (successfully). The only problem I can see is that you lose testdisk once you power down from the live session, unless you use a live USB with persistence.

I have no idea why the OP can't find testdisk - it's in the repos - but perhaps you're right to recommend a live testdisk utilty. I've already posted the link to Parted Magic.

---

### Post by ugruntu on 2010-10-29
so i've installed testdisk and run it. i picked analyse/ quick search/ then i highlighted the linux partition and the options on left/ right arrows are: P (green) and *(white).

i have once picked (P)green, i "wrote table", restarted nothing changed - got the grub error. then i restarted from live disk, reinstall testdisk got to the same place, picked the white one (*), changed the windows partition to (P), hit write. it told me done, i have to restart, i did restart same error. WTF?

anybody care to take me through a step-by step here?   


it found the partition, but when

---

### Post by ugruntu on 2010-10-29
so i've installed testdisk and run it. i picked analyse/ quick search/ then i highlighted the linux partition and the options on left/ right arrows are: P (green) and *(white).

i have once picked (P)green, i "wrote table", restarted nothing changed - got the grub error. then i restarted from live disk, reinstall testdisk got to the same place, picked the white one (*), changed the windows partition to (P), hit write. it told me done, i have to restart, i did restart same error. WTF?

anybody care to take me through a step-by step here?

---

### Post by ugruntu on 2010-10-29
Anyone?

by the way - in a dual-boot system configurated like mine (Windows, Ubuntu, Swap), which of these partition is the bootable? and should the  other ones be primary or logic partitions?

i really hope i get this sorted, although slowly i realize i have spent more time trying to solve it than it would have probably taken to reinstall everything from scratch. 

help?

---

### Post by ugruntu on 2010-10-29
i solved the problem. it wasn't easy, but i used testdisk first then i had to purge and re-create grub2. this helped a lot: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by prshah on 2010-10-29
> **ugruntu said:**
> which of these partition is the bootable? and should the  other ones be primary or logic partitions?

Usually, booting is done from the MBR (master Boot Record), which is before the partitions. The MBR then instructs which partition to boot from, or, as in this case, loads grub, which then handles further boot processing.

Booting can be done from either primary or logical partitions, when using GRUB.

I saw your messages later, by which time you had already solved the problem, but essentially, recovering the partition was not enough, you also need(ed) to re-install GRUB; I see that by now you have done this.

btw, I don't agree that it's faster to re-install afresh; the amount of data backup/restore and config time for a new install can stretch into days for me. I think it will be the same for you. Look upon the time spent in recovery as "learning time", so that when next you commit the same mistake (god forbid!) you will know exactly what to do to recover.

---

