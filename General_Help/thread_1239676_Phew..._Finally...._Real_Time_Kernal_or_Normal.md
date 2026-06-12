---
title: "Phew... Finally.... Real Time Kernal or Normal?"
date: 2009-08-13
forum: General Help
---

### Post by Shugs81 on 2009-08-13
Hi Chaps...

Been trying to read up on the real time kernal and can't work out how it differs from a normal kernal... is it just that it prioritises the program you are working from?

Just i've decided i'm sick of windows.... having a number of issues with it including the fact it seems to have ****** up the internet!!! logged me on here but when i tried to post said i needed to log on... and unable to make bank transactions from the same computer but able to from other ones!! but that's by the by...

I'm going to move over to a 64bit ubuntu but haven't decided about the real time kernal.... I wanted to do music recording and have seen that the real time kernal is the shizzle (well... peeps say so!) for it... but does it make a massive differnce to other programms? planning to run vm or something similar to have windows access but that's only for stuff i haven't got running in wine and Itunes... damn classic ipods with their encriptions!! otherwise i'd flac'ed up rather than alac'd up...

anyhow... simple choice... ubuntu studio 64 or normal ubuntu 64...

or is there a way to switch kernals to real time for when i want to record... bear in mind i've not been a fulltime user of linux for a while... can it be done via boot menu or just issuing a command in the terminal?

and how do i tell the differences between hard drives in the installlation menu so i know which one to wipe... I have a couple of partitions on each drive, having 1 sata and 1 ide...

cheers peeps! once it's on i won't be so lazy!:lolflag:

---

### Post by zvacet on 2009-08-13
>  I wanted to do music recording

If that is one of main task for your OS then install Ubuntu studio.

---

### Post by Arup on 2009-08-13
You can also consider installing OSS4 instead of ALSA that comes with regular Ubuntu, in that case, you won't need to use RT kernel as OSS4 has minimal latency compared to ALSA. You can find instructions for installing OSS4 at [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Shugs81 on 2009-08-14
the music recording used to be a priority but our lead guitarist went on a truly mental shopping spree after a promotion and spend about 5k on equipment!!!

I'm just going to use it for idea's mainly so it's more than likely going to be a small part of it... tho i'll look into that oss thing... seems quite interesting!

as to the hard drives.... am i right in thinking a sata drive is sda and an ide is hda? i've only really used ide drives in the past as the first sata drive i bought didn't work and i had it in my hand to test it and it set on fire! fun!

anyhow...

i have a back up partition ntfs on the ide which i want to keep and when the install menu comes up for partitioning i'm planning to wipe the sata drive and keep all the stuff on the ide drive... it's a 1tb sata drive and is currently patitioned windows/ubuntu studio/ntfs.... will these show as sda0 sda1 sda2??? an what are the reccomendations for new partition table? how big should the swap be and should i split up the rest of the drive? should i keep it all as one or should I have a separate media / docs / apps sort of thing?

---

### Post by P4man on 2009-08-14
Do a regular install then type: 

sudo apt-get install linux-rt

(or select it from the synaptic package manager)

that installs a "real time" kernel. And switching between them is as easy as selecting the kernel you want from the grub menu.

more info here:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by Shugs81 on 2009-08-14
that may be a good idea...

has the 64bit campatibility been ironed out? just cause i got 6gb ram in my system and with running xp notreally getting the benefit.... was there an open source vmware out there?

---

### Post by CatKiller on 2009-08-14
> **Shugs81 said:**
>  Been trying to read up on the real time kernal and can't work out how it differs from a normal kernal... is it just that it prioritises the program you are working from?

The real-time kernel scheduling is still pretty experimental. It's likely that things that can't be modified to run with it (like proprietary graphics drivers that need headers for a specific kernel) won't work. Open-source stuff is fine. You might get the occasional crash. Did I mention that it's experimental?


> 
or is there a way to switch kernals to real time for when i want to record... bear in mind i've not been a fulltime user of linux for a while... can it be done via boot menu or just issuing a command in the terminal?

Yes. Each version of the kernel that you install gets its own entry in GRUB. If you want to boot from an earlier kernel, or the real-time kernel, you just pick the appropriate entry from the GRUB menu.

> 
as to the hard drives.... am i right in thinking a sata drive is sda and an ide is hda?

Not necessarily. That used to be the way it was, but I think all hard drives are referred to as /dev/sd now.

You can always mount a partition to have a quick check of the contents if you want to be sure, though.

> 
an what are the reccomendations for new partition table? how big should the swap be and should i split up the rest of the drive? should i keep it all as one or should I have a separate media / docs / apps sort of thing?

The rule of thumb is that the swap should be twice the amount of RAM, up to a swap size of 2GiB. More than that is unlikely to be used. If you want to hibernate the computer, you'll need a swap size of at least as much as the amount of RAM that's used.

A number of people recommend having a separate /home partition for ease of re-installs.

The old habits of having specific filesystems for /boot and /var aren't that common any more.

If you're going to dual-boot between Ubuntu and Windows then having a partition for data that you want to be able to access from either of them is probably a good idea.

---

### Post by Shugs81 on 2009-08-15
wow... thanks for that...

wasn't planning on a dual boot... was gonna run some kind of virtual machine to use fm2009 via steam lol.... that's about all i wanted windows for!!

Just need to remember how to work linux now!!!:lolflag:

---

