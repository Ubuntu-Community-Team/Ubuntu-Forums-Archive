---
title: "Raid 5 Slow Performance"
date: 2010-04-29
forum: General Help
---

### Post by H1S0K4 on 2010-04-29
First of all I have to tell you that I'm still lacking Experience with Linux so pls be patient with me if I don't understand things right away :)

Here is my Problem: I have build a Raid 5 Array with 3 x 750GB Harddrives and whenever I try to write/read data to/from it the average transferrate is around 8-10 MB/s which is damn slow but I haven't figured out how to improve transfer speed. I can't give you detailed infos/stats right now since i'm at work and can't look it up, but if you have any ideas let me know :)

btw Speed remains the same even when I copy a file from one directory to another on the same array

Synchronizing took about 8 hours with around 24MB/s according to mdstat

Network shows no problem/errors (shouldnt matter anyway)

I tried different settings within Samba which didn't seem to make a big difference.

I once tried to reformat (ext3) the /dev/md0 which must have gone terribly wrong cause the transferspeed droped to 2-3 MB/s when writing but still around 6-8 MB/s reading

OS: Ubuntu Server 9.10

Hardware:
- AM2 - 4000+
- 4GB RAM
- 3 x 750 GB

---

### Post by itachisxeyes on 2010-04-29
are you using a Hardware RAID controller or a software RAID controller (I.E. Ubuntu)?

i'm not sure how many RAIDs you've managed before but, they need to run extra calculations when transferring data because of the stripped nature of the data. and if your using software to control that, then the calculation over-head is coming out of your main CPU and system memory.
where as a physical hardware RAID controller that is plugged into a PCI or some other extension port on your mobo actually has a dedicated CPU and memory to handled the calculations. 

also you never mentioned the make and model of the drives, so perhaps they are just "slow" in comparative to todays standards

---

### Post by ratcheer on 2010-04-29
In my strong opinion, based on working professionally with mid-range enterprise servers for more than 20 years, three drives is not enough to use for a reasonably performing RAID-5 array. Yes, it will "work", but performance will be bad. You need at least five drives for decent RAID-5 performance.

That said, I don't like RAID-5, anyway. I much prefer RAID 1+0 (aka RAID 10). You need at least four drives for that, and you have to increase in multiples of two.

Tim

---

### Post by charliehorse55 on 2010-04-29
You are copying files over a network? I am confused as to why you mention your network and your samba share. 

If you are copying it over the network, you're not going to get more than 50 MB/s with a Gigabit connection or 20 MB/s with a 100 Mb line.

---

### Post by H1S0K4 on 2010-04-29
@itachisxeyes: I'm using a Software Raid and I doubt the issue is hardware related, truth is I also have a 2nd Raid 5 Array installed with 5 x 1TB Drives which is not running atm to make sure it won't affect cpu usage until I figured how to improve performance. I didn't mention it to cause extra confusion :p

When both Arrays are active I can copy files from /raid1 to /raid2 and it still won't have a noticeable affect on the speed.

The 5 x 1TB used to be in another (slower) Computer with an older Ubuntu Dist. and the Computer back then could handle it better speedwise, unfortunately the person who set it up is not available anymore and I deleted the Superblocks when I installed them into my newer Computer so I had to rebuild everything from scratch. Even the bigger Raid performs about the same than the smaller one

My Drives:

5x Western Digital Caviar Black
HD 1000GB WD1001FALS, SATA-300, 7200rpm, 8.9ms, 32MB

3x Western Digital  Caviar Green
HD 750GB WD7500AADS, SATA-300, 7200rpm, 8.9ms, 32MB 

@ratcheer: I thought about Raid 10 before but I don't want to spend to much money, and I'm sure I'll add some more HDDs later. Right now I got 8 drives out of 12 possible installed

@charliehorse55: The Computer should act as a dedicated Fileserver with some extras which are not included at that point. I use Samba for Filesharing. I thought at first that Samba or the Networking might be the problem but after trying to write/read data directly on the Server and from different sources (ex. external HDD) I can say that those are not at fault.

---

