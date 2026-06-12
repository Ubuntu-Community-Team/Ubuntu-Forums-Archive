---
title: "Performance tuning for low end hardware"
date: 2010-01-12
forum: General Help
---

### Post by DMcCunney on 2010-01-12
Hi, folks::

I'm relatively new to Ubuntu, but not to Linux.  I started on Unix variants in the AT&T System V Release 2 days, have used several flavors of "real" Unix, and Red Hat, CentOS, SUSE, Puppy and other flavors of Linux.

I've seen a fair bit of info on-line for tuning Ubuntu, but it all assumes you have more than the minimum requirements, and tells you how to get Ubuntu to take advantage of additional resources, like RAM.  I have the opposite problem.  I have Ubuntu on low-end hardware.

I was given a Fujitsu Lifebook p2110 by the mother of a friend.  It had served her faithfully for years, and she loved it and didn't want to simply throw it out, but she had upgraded to a newer machine.  She considered me a good home for it, but  commented it was "slow slow slow".

Well, no surprise.  The Lifebook dates from 2001.  It had an 867mhz Transmeta "Crusoe" processor, a slow (UDMA 2 18MB/sec xfer rate) Toshiba hard drive, and 256MB of RAM, expandable to 384MB. It came from Fujitsu with Windows XP Pro SP2 installed.  XP wants 512MB of RAM to even *think* about performing.  You grew old and gray waiting for it to boot, and older and grayer waiting for programs to load.  It spent more time swapping than doing useful work.

It looked like a good candidate for a Linux distro.  So I swapped in a 40GB Fujitsu drive with similar low end specs from my SO's dead laptop, and repartitioned to triple boot.  It has Windows 2000 Pro SP4 (which is a *bit* faster in 256MB,) Puppy Linux 4.31, and Xubuntu 9.10, multi-booting from Grub.

Win2K is glacially slow, but that was expected.  It's there for when I must do something in Windows, and since Linux can read NTFS file systems, serves as a repository for various data.

Puppy itself is fairly sprightly.  It's intended for lower end systems, and the devs place a premium on small size.  (Puppy users have reported running it on a P200 with 64MB RAM for limited uses.)  The full distro is just over 100MB.  Third party apps are another matter.  Firefox 3.5, for instance, took 45 seconds to load and initialize.  Opera 10 took about 20, but the one packaged for Puppy was built static and was essentially one big executable the system could load in a continuous read.  FF 3.5 links against an assortment of external libs, and can't be built static, so it gets hobbled by seek time and low disk throughput.

Xubuntu 9.10 runs, but is *extremely* sluggish.  It's much slower than Puppy, and the same applications installed under Puppy load a lot slower under Xubuntu.

Puppy 4.31 uses a current kernel and supports ext4, so I used it when I upgraded from 4.12.  I saw a gratifying approximately 1/3 decrease in load times for apps, so it appears the ext4 performance claims are correct. I also converted the Xubuntu partition, by copying the tune2fs command over to the Puppy partition, booting to Puppy, and running it from there.  It helped a bit, but performance is still poor.

Does anyone have suggestions for optimizing Xubuntu for the box?  I know the first suggestion will be "add RAM", but that is unlikely to happen.  Expansion memory exists but is expensive, and part of my goal with this machine is seeing how much performance I can wring out of limited hardware *without* spending money on it.

Thanks in advance.
______
**Dennis**

---

### Post by oldos2er on 2010-01-12
There is so much of Gnome in Xubuntu, in my opinion it negates any "lightness" Xubuntu might have possessed.

You might want to look into LXDE. [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

[http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html](http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html)

[https://wiki.ubuntu.com/LXDE](https://wiki.ubuntu.com/LXDE)

or just stick with Puppy.

---

### Post by DMcCunney on 2010-01-12
> **oldos2er said:**
> There is so much of Gnome in Xubuntu, in my opinion it negates any "lightness" Xubuntu might have possessed.

You might want to look into LXDE. [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

[http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html](http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html)

[https://wiki.ubuntu.com/LXDE](https://wiki.ubuntu.com/LXDE)

or just stick with Puppy.
I'll look at LXDE, thanks.  Puppy comes with JWM as the lightest window manager they could find, but I use XFCE 4.6 by preference, and have Afterstep, Blackbox, Enlightenment, EvilWM, Fluxbox, IceWM, Openbox and a few other things for testing/playing.

I wouldn't mind using the same WM in both distros, but if LXDE offers a significant performance advantage, I'll think about it.

I *do* spend most time in Puppy, simply because performance is much better.  But it has quirks, lacks Ubuntu's auto-update, and has it's own package format, which means either living with a lesser selection, hacking to extract apps from other packages like RPM or DEB files and manually installing in Puppy, or hoping someone will make a PET file of the one you want.

I'd like to make more use of Xubuntu, but it's just too slow on the Lifebook.
______
**Dennis**

---

### Post by Cheesemill on 2010-01-12
Instead of using Xubuntu try doing a minimal install of Ubuntu then installing the xfce package, you'll end up with a distro that's alot lighter on resources.
I think RAM usage was around 80MB for the OS last time I tried this.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by DMcCunney on 2010-01-12
> **Cheesemill said:**
> Instead of using Xubuntu try doing a minimal install of Ubuntu then installing the xfce package, you'll end up with a distro that's alot lighter on resources.
I think RAM usage was around 80MB for the OS last time I tried this.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Thank you.  That looks quite promising.  It will have to wait a bit, as I need to check what the minimal CD leaves out, and will need to wipe and reinstall, but it looks like a good way to go down the road.  I don't know enough about Ubuntu yet to know what is bloat that can go away and what i need to keep, so I'm not going to try to manually prune it.

80MB sounds good, given the hardware I have.  I'll still be constrained by a slow HD, but it will be a considerable improvement.
______
**Dennis**

---

### Post by cascade9 on 2010-01-12
> **oldos2er said:**
> There is so much of Gnome in Xubuntu, in my opinion it negates any "lightness" Xubuntu might have possessed.

Agreed. 

> **Cheesemill said:**
> Instead of using Xubuntu try doing a minimal install of Ubuntu then installing the xfce package, you'll end up with a distro that's alot lighter on resources.
I think RAM usage was around 80MB for the OS last time I tried this.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This makes a big difference. Its worth a try.  

 I really wish that xubuntu was less 'gnome with an Xfce twist' and more 'pure' Xfce. But you know the saying, 'if wishes were horses then beggars would eat horsemeat'. Or something like that.

---

### Post by snowpine on 2010-01-13
Your specs are very, very low, and therefore I think Puppy is a better choice than anything in the 'Buntu family. I would also recommend checking out SliTaz; it has similar system requirements to Puppy, but is a lot "geekier" (which is a plus in my book).

---

### Post by DMcCunney on 2010-01-27
> **snowpine said:**
> Your specs are very, very low, and therefore I think Puppy is a better choice than anything in the 'Buntu family. I would also recommend checking out SliTaz; it has similar system requirements to Puppy, but is a lot "geekier" (which is a plus in my book).
Oh, there are lower end things.  Someone on the Puppy forums detailed how he got it up on an old Toshiba box that had run Win95 and had a whopping *16* MB of RAM.  (Essentially, he stripped out just about everything, and built the Puppy image he planned to run on another box, then transplanted to the target system.

For that matter, my first Unix system (which I still have), was an AT&T 3B1.  It was the high end of AT&T's UNIX-PC line from the 80s, intended to compete with the IBM PC.  The UNIX-PC was a Convergent Technologies (now part of Unisys) designed workstation, using a 10mhz Motorola 68010 CPU.  It would boot and run AT&T Unix System V Release 2, a full multiuser, multitasking OS, in **one** *megabyte* of RAM (yes, you read that right...) and perform useful work with acceptable performance.  Give it more (up to a max of 4MB) and it flew.  (I have 3.5MB.)  I'm continually bemused by current hardware requirements...

SliTaz is on my "look at when I get a moment" list.  I've seen references to it elsewhere as well.  Geekier doesn't bother me.  Puppy is fun, and runs on low end kit, but still has some very rough edges.
______
[B]Dennis
[/B]

---

### Post by DMcCunney on 2010-01-27
> **Cheesemill said:**
> Instead of using Xubuntu try doing a minimal install of Ubuntu then installing the xfce package, you'll end up with a distro that's alot lighter on resources.
I think RAM usage was around 80MB for the OS last time I tried this.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
And in fact, I did just that, in the process of upgrading Puppy to v4.31.  It helped a lot.  Puppy is still sprightlier, but Ubuntu installed that way is actually usable on the Lifebook.

Thanks for the suggestion!
______
**Dennis**

---

### Post by snowpine on 2010-01-27
Cool story but remember the first version of Ubuntu came out in 2004 and was optimized for the typical desktop hardware of its time. No version of 'Buntu will run on a 10mhz processor with 1mb of ram. ;)

---

### Post by t4thfavor on 2010-01-27
Very few linux's will run on something that slow, In fact I would probably say you would die of old age while compiling one of todays kernels on that PC :)

I was going to say install the minimal, and then only add the WM that you want, no Java, no Mono, none of the cruft that makes it so heavy. 

The server install ate about 100MB or ram at boot, but I might have caught it after it started caching. I had full ubuntu on a p3 600 with 128mb of ram, with the gnome removed, and xfce installe. It was usable but barely.

You should at a minimum see if you can scrounge that other 128mb of ram, it will save you loads of time.

---

### Post by DMcCunney on 2010-01-27
> **snowpine said:**
> Cool story but remember the first version of Ubuntu came out in 2004 and was optimized for the typical desktop hardware of its time. No version of 'Buntu will run on a 10mhz processor with 1mb of ram. ;)
I'd hardly expect *any* version of Linux to run in 1MB.  I just shake my head in wonder.  

I still have my first PC (acquired after my 3B1) sitting on a shelf.  It had a motherboard with a 10mhz NEC v20 CPU (an Intel 8088 compatible with improved microcode that would run code compiled for the 80186).  It had 640KB of RAM, with an Ast 6-Pak add-on card with 1 MB of EMS memory, split between 512K RAMdisk, 256MB of disk cache, and 256MB of EMS for programs that could use it.  A utility mapped video RAM to MS-DOS, so the box had 704KB of DOS memory.  Iy had two 360K 5.25" floppies and two Seagate ST-225 20MB hard drives.  My Palm OS PDA has a 200mhz ARM CPU, 128MB of RAM, and two 2 GB SD cards.  Back in the day, I felt constrained by 640KB or RAM.  Today, I feel constrained by 640 **MB**...
______
**Dennis**

---

### Post by t4thfavor on 2010-01-27
> **DMcCunney said:**
> I'd hardly expect *any* version of Linux to run in 1MB.  I just shake my head in wonder.  

I still have my first PC (acquired after my 3B1) sitting on a shelf.  It had a motherboard with a 10mhz NEC v20 CPU (an Intel 8088 compatible with improved microcode that would run code compiled for the 80186).  It had 640KB of RAM, with an Ast 6-Pak add-on card with 1 MB of EMS memory, split between 512K RAMdisk, 256MB of disk cache, and 256MB of EMS for programs that could use it.  A utility mapped video RAM to MS-DOS, so the box had 704KB of DOS memory.  Iy had two 360K 5.25" floppies and two Seagate ST-225 20MB hard drives.  My Palm OS PDA has a 200mhz ARM CPU, 128MB of RAM, and two 2 GB SD cards.  Back in the day, I felt constrained by 640KB or RAM.  Today, I feel constrained by 640 **MB**...
______
**Dennis**
Yes we all know 640k will be enough for anybody...

---

### Post by DMcCunney on 2010-01-27
> **t4thfavor said:**
> Very few linux's will run on something that slow, In fact I would probably say you would die of old age while compiling one of todays kernels on that PC :)
Puppy uses a 2.6 kernel, and is fairly sprightly.  (It's intended for low end kit, and the devs are always looking for tinier programs to substitute in the base install.) Third-party apps like Firefox 3.6 or Open Office 3.2 are a lot slower, but the sloth is in load time, and the constraint is a slow (UDMA 4) HD with anemic throughput.

> I was going to say install the minimal, and then only add the WM that you want, no Java, no Mono, none of the cruft that makes it so heavy.I don't consider Java "cruft", but then, I run things like the Eclipse IDE which is written in it.  No Mono at this point, largely because I don't have anything installed that needs it. 

But I did install from the MinimalCD, the added Xfce and other things manually.  It's still slow, but usable.

> The server install ate about 100MB or ram at boot, but I might have caught it after it started caching. I had full ubuntu on a p3 600 with 128mb of ram, with the gnome removed, and xfce installed. It was usable but barely.I wouldn't have tried to do a server install on that hardware.  Props to you for making it usable at all.

> You should at a minimum see if you can scrounge that other 128mb of ram, it will save you loads of time.If I happen across it free, I'll happily pop it in.  But buying compatible RAM for this box is expensive, and I could get about 4GB of DDR RAM for my desktop for what  a 128MB module for the Lifebook goes for.

I got the box free, and the challenge is to see what performance I can wring out of it *without* spending money on hardware.
______
**Dennis**

---

### Post by t4thfavor on 2010-01-27
What does it take, I have a large box of old mem, and I would be happy to mail it over for the cost of post if I had it.

And the server kernel has a slower event timer, which translates to a few less cycles used, and a bit more latency in the UI, but it does work decently as it has NOTHING installed.

---

### Post by t4thfavor on 2010-01-27
Oops

---

### Post by DMcCunney on 2010-01-27
> **t4thfavor said:**
> Yes we all know 640k will be enough for anybody...
Blame IBM, for choosing to reserve RAM above 640K for the system.  I recall the chap who wrote what became MS-DOS (Seattle Computer Product's 86DOS) had some snarky things to say about the design decision...

But I was around when Lotus 1,2,3 was single-handedly forcing everyone to upgrade from 256KB of RAM to 640KB to accommodate enormous Lotus worksheets.

Now Photoshop forces everyone to throw GBs of RAM at it  manipulate giant digital images.  (I have an older version of Photoshop.  It was the only image tool I had that would even open a giant TIFF file that originally came from the Hubble telescope.  NASA offered the same thing as a much smaller JPG, and stated the big mfile would be useful only to researchers.  I grabbed it to test because a correspondent elsewhere was having problems with it.  When I asked why he got it, it turned out he was an amateur astronomer, and wanted to get the huge file and slice it into pieces that would be used by another precess.  He was having issues just getting the file.)
______
**Dennis**

---

### Post by DMcCunney on 2010-01-27
> **t4thfavor said:**
> What does it take, I have a large box of old mem, and I would be happy to mail it over for the cost of post if I had it.
[http://www.memoryx.net/fulipme2.html](http://www.memoryx.net/fulipme2.html)

If you have either module, I'll happily reimburse you for postage, or provide a FedEx # for shipping.

> And the server kernel has a slower event timer, which translates to a few less cycles used, and a bit more latency in the UI, but it does work decently as it has NOTHING installed.So what does it do?
______
**Dennis**

---

### Post by t4thfavor on 2010-01-27
It was a dialup server when I had *GaSP* dialup... It also had a LAMP stack on it so I could teach myself PHP. Later on I installed asterisk... and then the cdrom died (slim) so I couldn't reload it anymore times :)

Those are weird memory modules, I have nothing of the sort. I have a lot of old SO dimm's from as far back as my off brand cyrux 200mhz lappy but nothing exotic, just normal ones. I tend to keep memory as I always find out that I need it for something later on.

---

### Post by DMcCunney on 2010-01-27
> **t4thfavor said:**
> It was a dialup server when I had *GaSP* dialup... It also had a LAMP stack on it so I could teach myself PHP. Later on I installed asterisk... and then the cdrom died (slim) so I couldn't reload it anymore times :)
I remember dial up.  I moved to DSL as my first broadband because that was what was available where I was.  When cable modem service became available, I switched, but kept the DSL as a high speed backup for some time.  :P

> Those are weird memory modules, I have nothing of the sort. I have a lot of old SO dimm's from as far back as my off brand cyrux 200mhz lappy but nothing exotic, just normal ones. I tend to keep memory as I always find out that I need it for something later on.I didn't think you would have compatible RAM.  The Fujitsu is a weird little notebook.  I don't think their memory modules are compatible with anything else.

My Linksys WRT54G router died a few weeks ago, and I shifted to an old Belkin as a backup.  The WRT54G model I have used a Linux kernel, and I saw details on line from a guy who manged to get Asterisk up and running on it.  It was on my to do list, but has to be postponed now...
______
**Dennis**

---

### Post by t4thfavor on 2010-01-27
I'm a semi active member over at [www.linksysinfo.org](www.linksysinfo.org) I have been through it all, asterisk doesn't tend to run well unless you have the 32MB ram model, and it barely fits if you only have 4mb of flash :) you can get about 4 calls (concurrent) before it falls on it's face.

It's got a 200mhz chip, and it takes about 3-4 hours to compile the firmware image on a amd athalon 3000+ W/3GB of ram :)

Have you gotten anywhere on the minimal install, or the puppy upgrade, I am kind of curious to see if you get this thing working to a usable standard.

---

### Post by DMcCunney on 2010-01-27
> **t4thfavor said:**
> I'm a semi active member over at [www.linksysinfo.org]("http://www.linksysinfo.org") I have been through it all, asterisk doesn't tend to run well unless you have the 32MB ram model, and it barely fits if you only have 4mb of flash :) you can get about 4 calls (concurrent) before it falls on it's face.
I didn't expect to try to *use* it as a PBX.  It was mostly just to learn about it, and a matter of "Why?  Because I *can!*" :)

> It's got a 200mhz chip, and it takes about 3-4 hours to compile the firmware image on a amd athalon 3000+ W/3GB of ram :)Yeah, I know the specs on the Linksys.  I saw people doing insane overclocking on them, but never had cause to bother.

I can believe the cross-compile times.  I'd set it up, do a make, and go to bed...

> Have you gotten anywhere on the minimal install, or the puppy upgrade, I am kind of curious to see if you get this thing working to a usable standard.Yes to both.  There was nothing on Puppy or Xubuntu I really needed to save, so I wiped both partitions and rebuilt from scratch.  Puppy is at v4.31 running on an ext4 file system, and I installed Ubuntu 9.10 on ext4 from the MinimalCD to get a base system and command line, then used apt-get to get Xfve4 and added from there.

Puppy works well, if quirkily, and Ubuntu is now usable.  It's slower to boot than Puppy, but not much slower once up, and ballpark guesses have disk throughput about 1/3rd better since shifting to ext4 because of better extent handling.

I can live with the speed (or lack of it).  The Lifebook was a gift, and it's mostly been an exercise in seeing what I could get out of old hardware without throwing money at it.
______
**Dennis**

---

### Post by sandy8925 on 2010-02-14
Try compiling the kernel ! Obviously on  another (much)faster machine. Should help. For help on that see the Master Kernel Thread somewhere here. You can also try fluxbox which is lightweight and loads fast. 256 MB RAM should be enough because I run Ubuntu (with gnome) on a desktop with 256 MB RAM (but having a Pentium 4 and a Geforce 6600 GT).

---

### Post by DMcCunney on 2010-02-14
> **sandy8925 said:**
> Try compiling the kernel ! Obviously on  another (much)faster machine. Should help. For help on that see the Master Kernel Thread somewhere here. You can also try fluxbox which is lightweight and loads fast. 256 MB RAM should be enough because I run Ubuntu (with gnome) on a desktop with 256 MB RAM (but having a Pentium 4 and a Geforce 6600 GT).
I may do that at some point.  I have Ubuntu 9.10 in a triple boot on mydesktop with Win2K and XP, and it's a 1.8ghz box with 4GB RAM and much faster drives.

I have Fluxbox on the Puppy slice on the Lifebook (and Afterstep, Blackbox, Enlightenment, Fwwm, IceWM, OpenBox and WindowMaker) so I have WMs to play with.

I like Xfce4 and will likely stick to it.  The big hobble on the Lifebook isn't RAM, it's a slow HD with anemic xfer rate, and it's not clear how much a recompiled kernel or a lighter WM would really help.
______
**Dennis**

---

