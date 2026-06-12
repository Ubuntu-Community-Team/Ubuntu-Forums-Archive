---
title: "Which laptop should i get?"
date: 2011-12-11
forum: General Help
---

### Post by ramus313 on 2011-12-11
i cant decide which one to get. i will be running ubuntu as my main OS, but i definitely need to be able to use Windows. i can get the 1st laptop with windows, then instal ubuntu on it, but would i have a problem with drivers and stuff like that? because the second one comes with ubuntu pre installed on it. ill be playing fairly intense games but the problem is most of them will be on the windows, so either ill be able to play them natively with a dual boot, or ill have to use a vm or wine. i will also be doing program development in rather large IDE's like eclipse.

1st: COMPAL NBLB5
01. Free Promotion : Limited Time Offer: Free Targus Backpack (it was $79.99)
02. Display : 15.6'' Full HD LED (1633x768) with Super Glossy Surface w/ 1.3MP Webcam.
03. Processor : Intel Core i7-720QM (1.60~2.8GHz, 45W) w/6M L3 Cache - 4 Cores, 8 Threads.
04. Thermal Paste : Standard Thermal Compound Paste - FREE IC Diamond 24 to CPU + GPU w/CPU Upgrade ONLY
05. Video : ATI MOBILITY RADEON HD 4650 Graphics with 1GB GDDR3 Memory.
06. Memory : 8GB (2x4GB) DDR3-1333 SO-DIMM (+$60)
07. Hard Drive : 500GB 7200 rpm SATA II - Seagate NCQ XT Hybrid w/4GB SSD (+$65)
08. Optical Drive : 4X Blu-Ray Reader/ 8X DVDRW/CDRW Super Multi Combo Drive (+$54)
09. Windows 7 Home Premium  
this question may sound kind of stupid, but i dont really know the difference between 32 & 64 bit operating systems, so which should i get?

2nd: Gazelle Professional
Ubuntu 11.10 64 bit
5 Free GB of Ubuntu One Online Storage and Sync
15.6" Full HD LED Display with Matte Finish Surface (1920 x 1080)
Nvidia GeForce GTX 560M Graphics with 1.5GB GDDR5 Video Memory
2nd Generation Intel Core i5-2430M Processor ( 3MB L3 Cache, 2.40GHz )
8 GB Dual Channel DDR3 SDRAM at 1333MHz - 2 X 4GB 
500GB 7200rpm SATA Hybrid Hard Drive with 4GB SSD 
8X DVD±R/RW/4X +DL Super-Multi Drive
Internal 802.11 B+G+N Wireless LAN + Bluetooth Combo Module



p.s. the battery life is important to me, but i dont really need it any more then 2-3 hours



P.S.s should i get an 80gb SSD and my external 1TB harddrive, or the 500 gb 4gb SSD Hybrid?

---

### Post by WasMeHere on 2011-12-11
Hi ramus313,

I suggest you buy the one with Ubuntu preinstalled. That way you get hardware that co-operates well with your main operating system (for example nVidia instead of ATI graphics).

With 8 GB RAM you should definitely choose 64-bit OS.

I had not heard of hybrid drives before, it looks interesting. I think you will get tired of 'always' using an external drive, but if you can squeeze everything you need often into an 80 GB SSD, that is also a good option.

I don't know anything about the battery life of these computers. What information can you get from the vendors and from the internet?

---

### Post by ramus313 on 2011-12-11
> **Olle Wiklund said:**
> Hi ramus313,

I suggest you buy the one with Ubuntu preinstalled. That way you get hardware that co-operates well with your main operating system (for example nVidia instead of ATI graphics).

With 8 GB RAM you should definitely choose 64-bit OS.

I had not heard of hybrid drives before, it looks interesting. I think you will get tired of 'always' using an external drive, but if you can squeeze everything you need often into an 80 GB SSD, that is also a good option.

I don't know anything about the battery life of these computers. What information can you get from the vendors and from the internet?

with the system 76 on i have heard anything from 1 hour to 3.5 hours, but im not sure about the windows one.

do you think the ubuntu one could seamlessly run windows 7 in a vm machine with those specs, and even play fairly intense games on the vm without lag (CoD, FIFA stuff like that?)?

---

### Post by WasMeHere on 2011-12-11
> **ramus313 said:**
> with the system 76 on i have heard anything from 1 hour to 3.5 hours, but im not sure about the windows one.

do you think the ubuntu one could seamlessly run windows 7 in a vm machine with those specs, and even play fairly intense games on the vm without lag (CoD, FIFA stuff like that?)?

I suggest you play the games natively with a dual boot of Windows. A virtual machine slows things down, and only a small percentage of the games play well in Wine.

---

### Post by ramus313 on 2011-12-11
> **Olle Wiklund said:**
> I suggest you play the games natively with a dual boot of Windows. A virtual machine slows things down, and only a small percentage of the games play well in Wine.

i was under the impression that it was very difficult to dual boot with windows when ubuntu was installed first.  does windows automatically erase the drive?  if so it will be difficult because system 76 manually installs all the drivers and i wont really know what im doing

---

### Post by CryptAck on 2011-12-11
Personally, I think it would be better to determine which is more important to you: running the games on Windows 7 or having Ubuntu work without worry. 

I have an HP DV6T with a i7-720QM, 1GB Nvidia GT 320M, and 8GB of memory. Gaming, at a decent resolution, is becoming very difficult on the machine. Your options listed do have better video cards than mine, but the ATI 4650 is still middle of the road. I've always ran games on a native Windows 7 environment, I would expect a degraded performance on a VM. CoD MW3 does not perform ideally given the current specs I have.

In my opinion, if you are looking for a good machine to run Ubuntu, the System76 is the best choice. For gaming, I'd consider other options though.

---

### Post by CryptAck on 2011-12-11
> **ramus313 said:**
> i was under the impression that it was very difficult to dual boot with windows when ubuntu was installed first.  does windows automatically erase the drive?  if so it will be difficult because system 76 manually installs all the drivers and i wont really know what im doing

This maybe something you could work out with the System76 staff.

Also, you are correct that it is more difficult, but it's not "very difficult". You would need to install Windows 7 to a different partition and then re-install GRUB and create the Windows 7 entry.

---

### Post by WasMeHere on 2011-12-11
> **ramus313 said:**
> i was under the impression that it was very difficult to dual boot with windows when ubuntu was installed first.  does windows automatically erase the drive?  if so it will be difficult because system 76 manually installs all the drivers and i wont really know what im doing
The easy way with a new machine is to wipe the disk and install Windows first. Then you install Ubuntu (which is fast and easy). With a new machine you lose very little doing it that way (maybe an hour if you know what to do).

I suggest that you preconfigure your hard drive from a live CD or USB drive before installation (deciding partition types and sizes). Then install Windows, and finally Ubuntu.

If Ubuntu is installed, you can still create a partition (but it must be a primary partition) for Windows. The master boot record will be overwritten by Windows during installation, but that can be fixed fairly easily afterwards so that you can run grub and perform the dual booting.

---

### Post by ramus313 on 2011-12-11
> **CryptAck said:**
> This maybe something you could work out with the System76 staff.

Also, you are correct that it is more difficult, but it's not "very difficult". You would need to install Windows 7 to a different partition and then re-install GRUB and create the Windows 7 entry.

yea but im worried because i know system 76 installt drivers and such to make the hardware complely compatible with ubuntu and i dont want to run into any problems when re installing ubuntu

---

### Post by WasMeHere on 2011-12-11
> **CryptAck said:**
> This maybe something you could work out with the System76 staff ...
This may turn out to be the best option :-) But make sure that the partition sizes will be sufficient for both systems. It might also be a good idea to create a common ***data*** partition with ntfs.

The only partition that need to be primary is the windows one. Linux, swap and the data partitions can be logical partitions inside an extended partition.

---

### Post by ramus313 on 2011-12-11
> **Olle Wiklund said:**
> This may turn out to be the best option :-) But make sure that the partition sizes will be sufficient for both systems. It might also be a good idea to create a common ***data*** partition with ntfs.

The only partition that need to be primary is the windows one. Linux, swap and the data partitions can be logical partitions inside an extended partition.

if i ask them could they do it for me? that would be great

---

### Post by WasMeHere on 2011-12-11
> **ramus313 said:**
> if i ask them could they do it for me? that would be great
Yes, it costs nothing to ask ;-) But ask also what it would cost with this 'custom installation' and compare it to the cost of a standard installation plus a Windows install disk!

---

### Post by CryptAck on 2011-12-11
> **ramus313 said:**
> yea but im worried because i know system 76 installt drivers and such to make the hardware complely compatible with ubuntu and i dont want to run into any problems when re installing ubuntu

If you perform the installation correctly, no data loss on the Ubuntu side should occur. Technically, the MBR would be overwritten and GRUB would need to be re-installed, but this does not impact any System76 installed drivers. 

The actually process is more involved than the standard "install Windows then install Linux", but if you follow the instructions it should go just as smoothly.

---

### Post by ramus313 on 2011-12-11
> **CryptAck said:**
> If you perform the installation correctly, no data loss on the Ubuntu side should occur. Technically, the MBR would be overwritten and GRUB would need to be re-installed, but this does not impact any System76 installed drivers. 

The actually process is more involved than the standard "install Windows then install Linux", but if you follow the instructions it should go just as smoothly.

what exactly is the process? i have tried installing windows on my ubuntu desktop, and i could not get it to install correctly

---

### Post by gman16000 on 2011-12-11
i just purchased the gazelle professional. after i got it, i decided i wanted to remove the cd drive and put in a 2nd hard drive. they sent me drive cover and i installed my own drive.

on the 2nd physical drive, i installed windows. now i just change the boot order in the bios when i want to switch between the ubuntu / windows.  that way, i dont really have to mess around with grub and i get more storage space too. and i really never use a cd drive anymore.

if you do go gazelle professional, i highly recommend going with either Intel Centrino for the wireless.  i bought the cheaper internal wireless and it was spotty with all my routers. they sent me an intel 6230 and that works great!!

---

### Post by ramus313 on 2011-12-11
> **gman16000 said:**
> i just purchased the gazelle professional. after i got it, i decided i wanted to remove the cd drive and put in a 2nd hard drive. they sent me drive cover and i installed my own drive.

on the 2nd physical drive, i installed windows. now i just change the boot order in the bios when i want to switch between the ubuntu / windows.  that way, i dont really have to mess around with grub and i get more storage space too. and i really never use a cd drive anymore.

if you do go gazelle professional, i highly recommend going with either Intel Centrino for the wireless.  i bought the cheaper internal wireless and it was spotty with all my routers. they sent me an intel 6230 and that works great!!

how did you install windows without a cd? via online downloads?  i dont know if i can sacrifice the cd drive, but that is actually a great idea. i mean i do have an external hardrive and a desktop with a cd drive so i guess i dont need one on my laptop but i dont know... which harddrives did you use?

---

### Post by CryptAck on 2011-12-11
> **ramus313 said:**
> what exactly is the process? i have tried installing windows on my ubuntu desktop, and i could not get it to install correctly

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

That has some general information on it. 

As for the exact process, it'll depend on your hard drive partition setup. Usually re-sizing is necessary, but it depends. 

Once you've chosen a new laptop, create a new thread requesting help on dual-booting and users here will help get you up and running.

---

### Post by gman16000 on 2011-12-11
> **ramus313 said:**
> how did you install windows without a cd? via online downloads?  i dont know if i can sacrifice the cd drive, but that is actually a great idea. i mean i do have an external hardrive and a desktop with a cd drive so i guess i dont need one on my laptop but i dont know... which harddrives did you use?

i have a external USB cd drive that i share between computers since none of my computers have cd drives (except the mac).

one drive is the 128GB ssd intel that system 76 ships (a good drive by the way) and the other is an 128GB ssd ocz-vertex3 that i bought at newegg.

---

### Post by ramus313 on 2011-12-11
thats a good idea too, the external dvd drive. but heres a question, if i get the 500gb 4gb SSD hybrid, does the windows partition share 2gbs of the cashe for the SSD thing? it sounds kind of confusing dual booting with that drive.

---

### Post by WasMeHere on 2011-12-11
> **ramus313 said:**
> thats a good idea too, the external dvd drive. but heres a question, if i get the 500gb 4gb SSD hybrid, does the windows partition share 2gbs of the cashe for the SSD thing? it sounds kind of confusing dual booting with that drive.
Browse the internet to find out about that hybrid drive, an if you find nothing, ask the vendor! I think there should be some (internal?) logic to get optimal performance.

---

