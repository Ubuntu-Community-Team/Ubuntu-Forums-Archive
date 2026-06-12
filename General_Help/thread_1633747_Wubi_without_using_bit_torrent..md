---
title: "Wubi without using bit torrent."
date: 2010-11-29
forum: General Help
---

### Post by Malacath on 2010-11-29
Is there a way to get Wubi to not use bit torrent?

My ISP(BT Broadband) hates bit torrent and throttles them to below dial-up speed.

Every time I try running Wubi it tries to get the iso through bit torrent. Which will take 100 hours due to throttling.

I have tried downloading the ISO separately and putting that in the same folder as wubi but wubi ignores that and still tries to download it using bit torrent.

---

### Post by WorMzy on 2010-11-29
Make sure you're downloading the right iso. Last I heard, Wubi doesn't like 10.10, and will download 10.04 instead.

If it doesn't like the 10.04 iso either, then you could phone up your ISP and tell them to get their act together, or install Ubuntu to a partition (which is recommended anyway).

---

### Post by Malacath on 2010-11-29
> **WorMzy said:**
> Make sure you're downloading the right iso. Last I heard, Wubi doesn't like 10.10, and will download 10.04 instead.

If it doesn't like the 10.04 iso either, then you could phone up your ISP and tell them to get their act together, or install Ubuntu to a partition (which is recommended anyway).

Thanks. 

I had the ISO for 10.10 so that's probably why it doesn't work.
I'll download 10.04.

Partitioning is not an option. I don't want to mess with the partitions in case I mess it up. My laptop doesn't have a windows disc. All recovery files are on a hidden partition.

---

### Post by bodhi.zazen on 2010-11-29
You do not need to download an iso at all.

Go here :

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

click on the big orange "Start download" button.

Click the download, it will download wubi.exe

You can install it directly or save the wubi.exe to your desktop and run it later.

---

### Post by xadz on 2010-11-29
I had nothing but trouble using Wubi yesterday!  Got to the last few minutes of downloading and just hangs there, very irritating.  I'd steer away from it for now if I were you.  Good luck!

---

### Post by Slim Odds on 2010-11-29
> **Malacath said:**
> Thanks. 

I had the ISO for 10.10 so that's probably why it doesn't work.
I'll download 10.04.

Partitioning is not an option. I don't want to mess with the partitions in case I mess it up. My laptop doesn't have a windows disc. All recovery files are on a hidden partition.

Laptops like that also have a recovery utility that allows you to burn some DVD's to use to restore your system. You had better use it!.

If your hard drive dies, you are screwed otherwise. Burn the DVD's.

---

### Post by Malacath on 2010-11-30
> **Slim Odds said:**
> Laptops like that also have a recovery utility that allows you to burn some DVD's to use to restore your system. You had better use it!.

If your hard drive dies, you are screwed otherwise. Burn the DVD's.

Thanks.

Burned them earlier. I still prefered it when computers came with actual windows discs. Could format and partition the hard drive as much as I like back then.

---

### Post by Malacath on 2010-11-30
> **bodhi.zazen said:**
> You do not need to download an iso at all.

Go here :

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

click on the big orange "Start download" button.

Click the download, it will download wubi.exe

You can install it directly or save the wubi.exe to your desktop and run it later.

Unfortunately I did. The Wubi installer uses bit torrent to download the ISO. And my ISP which is probably one of the most popular in the UK throttles bit torrent to speeds similar to dial-up. 
So had no choice but to download the ISO separately.

Anyway. Got Ubuntu installed and running now.

---

### Post by mastablasta on 2010-11-30
Good. Just remember that Wubi si ment more to test the system. it is using a large file created on windows fiel system if something happens to that file you will loose the whole system and likely all dfata on it. also some updates and uprgades can mess it up.
 
have fun trying and don't be afraid to partition the disk. it's the first thing i do when i get a new computer (usually even befor einstalling the OS). separate the data and programmes. and create a backup partition.

---

### Post by Malacath on 2010-11-30
> **mastablasta said:**
> Good. Just remember that Wubi si ment more to test the system. it is using a large file created on windows fiel system if something happens to that file you will loose the whole system and likely all dfata on it. also some updates and uprgades can mess it up.
 
have fun trying and don't be afraid to partition the disk. it's the first thing i do when i get a new computer (usually even befor einstalling the OS). separate the data and programmes. and create a backup partition.

This is the second time i've tried Ubuntu.
It didn't work well on my old laptop so tried different linux distros.
That computer had a windows disc so I was using partitions. At one point I ended up totally messing up the computer although that was another linux and not Ubuntu. Must have messed up with the partitioning or something. Luckely I had the windows disc.


Anyway is there a good guide anywhere for beginners to get Ubuntu safely installed using partitions without messing up windows or the recovery partition?

Ubuntus running well on my current laptop so may end up wanting to install it without using wubi eventually.

---

### Post by bodhi.zazen on 2010-11-30
> **Malacath said:**
> Anyway is there a good guide anywhere for beginners to get Ubuntu safely installed using partitions without messing up windows or the recovery partition?

There is no "fool proof" method, there is always some risk with installing an operating system.

You can mitigate the risk by:

1. Back up your data.

2. Read the documentation before you start. Understand what you are doing.

Linux uses different terminology to refer to partitions then Windows.

See: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Personally, I fire up a live CD and run gparted -> do the physical partitioning -> then run the installer.

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by DogMatix on 2010-11-30
> **Malacath said:**
> Is there a way to get Wubi to not use bit torrent?

My ISP(BT Broadband) hates bit torrent and throttles them to below dial-up speed.

I have BT broadband and have no issues with bit torrents at all. I use them regularly.

---

### Post by Malacath on 2010-11-30
> **bodhi.zazen said:**
> There is no "fool proof" method, there is always some risk with installing an operating system.

You can mitigate the risk by:

1. Back up your data.

2. Read the documentation before you start. Understand what you are doing.

Linux uses different terminology to refer to partitions then Windows.

See: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Personally, I fire up a live CD and run gparted -> do the physical partitioning -> then run the installer.

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Thanks for those links. I'll check them out.

---

### Post by Malacath on 2010-11-30
> **DogMatix said:**
> I have BT broadband and have no issues with bit torrents at all. I use them regularly.

Must depend on your exchange. On my exchange they are throttled every evening and all weekend.
The FUP even says they throttle bit torrents

---

