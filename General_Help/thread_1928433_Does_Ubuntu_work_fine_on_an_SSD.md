---
title: "Does Ubuntu work fine on an SSD?"
date: 2012-02-20
forum: General Help
---

### Post by ComradeNF on 2012-02-20
So I have a 64GB Crucial M4 and I was wondering if it would be fine to install Ubuntu 11.10 64-bit onto it and put it in my Lenovo Z370 laptop. I'm currently running Windows 7 but I want to use Ubuntu for a month so I will be formatting my SSD (as to not get tempted to go back to Windows for the duration of the month).

So would Ubuntu work fine on the SSD? Or should I install it on a spare 5400 RPM drive that I have?

---

### Post by dcstar on 2012-02-20
> **ComradeNF said:**
> So I have a 64GB Crucial M4 and I was wondering if it would be fine to install Ubuntu 11.10 64-bit onto it and put it in my Lenovo Z370 laptop. I'm currently running Windows 7 but I want to use Ubuntu for a month so I will be formatting my SSD (as to not get tempted to go back to Windows for the duration of the month).

So would Ubuntu work fine on the SSD? Or should I install it on a spare 5400 RPM drive that I have?

[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

---

### Post by HavarN on 2012-02-20
I ran into a boot problem caused by the SSD initializing much faster than the HDDs in my mdadm RAID setup spun up. For details and a fix see this page: [http://www.bomski.com/2012/01/ubuntu-11-10-with-raidnot-booting-after-installing-mdadm-read-on/](http://www.bomski.com/2012/01/ubuntu-11-10-with-raidnot-booting-after-installing-mdadm-read-on/)

---

### Post by Grenage on 2012-02-20
> **ComradeNF said:**
> So I have a 64GB Crucial M4 and I was wondering if it would be fine to install Ubuntu 11.10 64-bit onto it and put it in my Lenovo Z370 laptop. I'm currently running Windows 7 but I want to use Ubuntu for a month so I will be formatting my SSD (as to not get tempted to go back to Windows for the duration of the month).

So would Ubuntu work fine on the SSD? Or should I install it on a spare 5400 RPM drive that I have?

I type this from an SSD installed on Friday; no problems.  dcstar's link is a good one, and well worth running through if you do use an SSD.

---

### Post by forrestcupp on 2012-02-20
I installed on an SSD and didn't have any problems at all. It's good to have these resources in case you do, though.

---

### Post by JCM_Pico on 2012-02-20
I there... 

I'm very interested in this thread. Since I about to buy a new laptop, and I only use Linux... Does it worth it to have an SSD or the price/advantages are negligible...

This runs into the question of ComradeNF :D

---

### Post by Grenage on 2012-02-20
An SSD is one of the best upgrades you can have, in my opinion; I would never go back to a mechanical drive.

---

### Post by oldfred on 2012-02-20
Backup your Windows. We seem to find many users who have one application that they cannot live without. It took me 3 years to wean myself from Quicken and use kmymoney.:) 

I also just installed a SSD, but have not fully implemented it yet as it is/will be my 12.04 install. For now just testing & works well. It is 60GB and I made two / (root) partitions so I can boot 2 different Ubuntus.

I used gpt as suggested by the arch site, and may get a new UEFI system so I left space for an efi partition as the first partition, created a small bios_grub partition and it installed without issue.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by forrestcupp on 2012-02-20
> **JCM_Pico said:**
> Does it worth it to have an SSD or the price/advantages are negligible...

The cost effective way to do it is to put your OS and most used programs on the SSD, and to use a larger HDD for all of your data and files, like music, pictures, and videos.

---

### Post by haqking on 2012-02-20
> **forrestcupp said:**
> The cost effective way to do it is to put your OS and most used programs on the SSD, and to use a larger HDD for all of your data and files, like music, pictures, and videos.

exactly.

I just built a new system and i got 2 x 128GB Crucial M4 SSD, One is for Windows (with new found interest in a few games now i am adddicted to SWTOR , god damn it !) and the second is for Linux (Slackware -Current and Debian Stable)

Both on 6GB SATA...coupled with 16Gb ram and a I7 2700K blistering performance.

I initially bought a 2TB HDD due to such low price for data, as they were so cheap i bought 2 more so got 3 x 2 TB HDD's for data, music, videos, Virtual machines etc and everything runs so quickly.

Slackware boot time = 12 seconds
Debian boot time = 15 seconds
Windows 7 boot time = for some reason it varies from about 15 to 25

I need to do some tweaking though as i have seen some faster boots so need to play a little when i get a minute

all from cold.

Awesomeness (apart from a recent brand new 580GTX failure but that is resolved tomorrow)

Well enough of me bathing in my glory...LOl

My point was SSD are worth every penny.

Thinking of going for a 256GB soon too as prices are so good right now

---

### Post by efflandt on 2012-02-20
I originally used my old 2006 laptop to install Ubuntu on 80 GB Intel SSD.  With SATA1 it was 4 times faster than the laptop's 5400 rpm drive.  On my desktop it was twice as fast at that, or twice as fast as a 7200 rpm SATA2 drive.  I forget if I ran 10.10 on it, but then ran Natty development until fed up with unresolved video issues at that stage.  Never did run Natty release

It is currently running 64-bit 11.10 which goes from grub menu to login in 8 seconds, and from there to desktop in under 2 more seconds.

---

### Post by dcstar on 2012-02-21
> **Grenage said:**
> An SSD is one of the best upgrades you can have, in my opinion; I would never go back to a mechanical drive.

I use a Seagate Hybrid drive that basically gives me SSD boot up and loading times, 750GB of storage and none of the hassles of managing a SSD.

I have used SSDs previously and the only place I use them now is in portable devices to save on power and extend battery life, the Hybrid drive is a far more cost-effective option.

---

### Post by Grenage on 2012-02-21
> **dcstar said:**
> I use a Seagate Hybrid drive that basically gives me SSD boot up and loading times, 750GB of storage and none of the hassles of managing a SSD.

I have used SSDs previously and the only place I use them now is in portable devices to save on power and extend battery life, the Hybrid drive is a far more cost-effective option.

I've heard good things about them, although I'd be more partial to using SRT with a smaller SSD and mechanical on the side.  I'm not sure what the hassles of SSD are though, I assume you're simply talking about cost?

I don't store data on my computers, that's all on storage servers with big, lumbering mechanicals. :)

---

### Post by dcstar on 2012-02-22
> **Grenage said:**
> I've heard good things about them, although I'd be more partial to using SRT with a smaller SSD and mechanical on the side.  I'm not sure what the hassles of SSD are though, I assume you're simply talking about cost?


Any SSD used in a Linux system *must* only have TRIM compatible filesystems installed on it otherwise using any non-compatible filesystem partition - like NTFS - will eventually use up all the empty blocks because no TRIM commands are ever run on those partitions.

Once the empty blocks are gone write performance goes down the toilet and can make having a SSD pretty pointless.

---

### Post by Grenage on 2012-02-22
> **dcstar said:**
> Any SSD used in a Linux system *must* only have TRIM compatible filesystems installed on it otherwise using any non-compatible filesystem partition - like NTFS - will eventually use up all the empty blocks because no TRIM commands are ever run on those partitions.

Once the empty blocks are gone write performance goes down the toilet and can make having a SSD pretty pointless.

But aren't all modern distros using trim-compatible filesystems and kernels?

---

### Post by dcstar on 2012-02-22
> **Grenage said:**
> But aren't all modern distros using trim-compatible filesystems and kernels?

EXTx is TRIM supported, BTFRS apparently is, AFAIK no others are.

Simply look at the mount command for each filesystem type, if there is no DISCARD option then you will have to manually run the hdparm **wiper.sh** command to release the blocks.

That is what I mean by "hassles".

---

### Post by Grenage on 2012-02-22
> **dcstar said:**
> EXTx is TRIM supported, BTFRS apparently is, AFAIK no others are.

Simply look at the mount command for each filesystem type, if there is no DISCARD option then you will have to manually run the hdparm **wiper.sh** command to release the blocks.

That is what I mean by "hassles".

At least that's the main systems covered; cheers for the elaboration.

---

### Post by Dondermans on 2012-04-29
> **dcstar said:**
> Any SSD used in a Linux system *must* only have TRIM compatible filesystems installed on it otherwise using any non-compatible filesystem partition - like NTFS - will eventually use up all the empty blocks because no TRIM commands are ever run on those partitions.

Once the empty blocks are gone write performance goes down the toilet and can make having a SSD pretty pointless.

I am considering a Samsung SSD (830-series, 256Gb). I read that performance goes down the drain if it is filled to the brim, but until I read the message I quoted, I though one could just choose to *not* partition the full capacity (e.g. leave a few Gbs unpartioned). Would that work?

I am currently using Ubuntu 11.10, and Windows XP, which is to be replaced by Windows 7 in the near future.

---

### Post by nogasbiker on 2012-05-10
> **Grenage said:**
> But aren't all modern distros using trim-compatible filesystems and kernels?Perhaps, but TRIM is not enabled by default.  It would be nice if installers detected SSDs, but they do not seem to be SSD aware.

I haven't checked 12.04 yet, but one has to manually alter the mount options for / and /home to enable TRIM.

---

### Post by nogasbiker on 2012-05-10
> **dcstar said:**
> EXTx is TRIM supported, BTFRS apparently is, AFAIK no others are.Please double check this.

I have read that only EXT4 supports it as a mount option.  EXT3 implements it partially-- only on an ioctl() basis for manually invoked garbage collection clis.  I've been happy with EXT3, but went out of my way to go to EXT4 when my SSD machine arrived.

[http://en.wikipedia.org/wiki/TRIM](http://en.wikipedia.org/wiki/TRIM)

---

