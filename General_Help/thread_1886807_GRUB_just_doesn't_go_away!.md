---
title: "GRUB just doesn't go away!"
date: 2011-11-25
forum: General Help
---

### Post by ubchris on 2011-11-25
I had Ubuntu Natty for a while to more or less stick my feet into Ubuntu. I wrote GRUB into the MBR. Biggest mistake EVER. 

Later, I decided school was coming up and I needed a stable system where I could have full compatibility with my programs. Literally reformatted my HDD and continued with my Windows installation. After a couple of power cycles, it gives me a GRLDR error at boot, saying that it can't find GRLDR and to press any key to boot into the previous MBR. 

I'm at a loss as to what to do next. 

I've tried:
--Using Rescatux to restore Windows bootloader
--Using the Natty LiveCD to use the dd command to delete the first 512 bytes of my HDD where my bootloader is
--Using the Windows terminal to run bootrec.exe commands
--Completely nuked and rebuilt my BCD using Windows commands

What else is there to do? It's funny because I can boot into Windows perfectly for the first couple of power cycles, but once that's over, it'll give me the GRLDR. So if it's a bootloader problem, how come it works the first few times after a fresh install? 

I'm really at my wits' end.

---

### Post by drs305 on 2011-11-25
Do you see a Grub menu first? If it's Grub or Grub 2, there will be a title at the top of the menu designating Grub 0.97 or Grub 1.96 or later.

"grldr" is not Grub, it's grub4dos. If you aren't seeing the Grub menu and selecting a Grub menuentry that is taking you to grldr, it's probably not a Grub problem.

I'm not a Windows user and have never used grub4dos so I can't offer much more than that. Investigate how grub4dos is set up and how to remove it and you may have found your answer.

---

### Post by bluexrider on 2011-11-25
You didn't state what version of Windows you are using. However what you need to do is "fix MBR"

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)


This may help.

Good luck

---

### Post by perspectoff on 2011-11-25
> **bluexrider said:**
> You didn't state what version of Windows you are using. However what you need to do is "fix MBR"

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)


This may help.



The advice in this link is old and not really very accurate.

The Master Boot Record does not point to an operating system, but to the location of the primary bootloader. One doesn't "write" Grub to the MBR. All that is written to the MBR is the location (on the hard drive) of the primary bootloader (whether that is the Windows bootloader or some version of the Grub bootloader).

That bootloader can be stored in its own partition (as newer versions of Windows 7 do and which can be done with Grub Legacy) or can be stored in the partition of the operating system (as is done with Grub2, which is used in current versions of Ubuntu).

The job of the Master Boot Record is only to designate where to find the primary desired bootloader. 

I have advocated for many years that a primary bootloader should be a stand-alone bootloader (such as Grub Legacy, aka Grub 0.96) and not require an OS to function (as Grub2 does). It should be located in its own partition and not be located in the same partition as any one OS.

That way the Master Boot Record can forever point to that single stand-alone bootloader residing in its own partition independent of any particular OS, and the types of problems the OP complains about (and which is an ever-present problem for Grub2 users) become non-existent.

If it is necessary to chainload either a Windows, Mac, or Linux (i.e. Grub2) bootloader, the primary bootloader (e.g. Grub Legacy) can do that.

One of the reasons Grub2 seems to have evolved was to accommodate virtual OS's and evanescent OS's on evanescent partitions. That might be a common scenario for datacenters, but for the average home or small business user, it is not. 

Despite constant flames, I have ditched Grub2 entirely this year (after escalating problems with it), going back 100% to Grub Legacy on all my systems.

It takes a small amount of work to create a stand-alone instance of Grub Legacy in its own partition, but after it is done, there is never the problem of being unable to boot ever again.

If you want to know the advice I used, it is here:

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

or

[http://kubuntuguide.info/index.php/Multiple_OS_Installation](http://kubuntuguide.info/index.php/Multiple_OS_Installation)

---

### Post by c.cobb on 2011-11-27
> **perspectoff said:**
> I have advocated for many years that a primary bootloader should be a stand-alone bootloader (such as Grub Legacy, aka Grub 0.96) and not require an OS to function (as Grub2 does). It should be located in its own partition and not be located in the same partition as any one OS.

This makes a lot of sense. One thing I'm not clear on: why does Grub2 require an OS to function? Do you mean for the /etc/grub.d/ and update-grub stuff? Once Grub2 is installed, isn't that merely for convenience, and couldn't the Grub2 grub.cfg file be edited directly (just as you must do with the Grub Legacy menu.lst file)?

I'm thinking that the primary boot loader partition would be a nice place to stuff ISO images that can be booted directly, and don't think that Grub Legacy allows for this while Grub2 handles this nicely.

---

### Post by alfalahi on 2011-11-27
start Ubuntu live CD

start internet

install Boot repair

click recommanded or fix cant remmber now

then when it finsh restart ur pc then start up windows

search youtube on how to fix windows boot

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

