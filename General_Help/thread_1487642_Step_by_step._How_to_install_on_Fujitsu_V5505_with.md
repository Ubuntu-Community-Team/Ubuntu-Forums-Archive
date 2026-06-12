---
title: "Step by step. How to install on Fujitsu V5505 with new hdd"
date: 2010-05-19
forum: General Help
---

### Post by stevenjo on 2010-05-19
Hi All,
Totally new to Ubuntu. I am also not totally a pro with PC's either so please don't go too deep.
 
Here is what i need help with.
 
I have a Fujitsu V5505 the hard drive is totally fried & I lost everything. I bought a HDD Dock to check it with same results FRIED.
 
I plan on buying a new hdd & installing ubutan as the OS.
 
I have done some googling & as with everything the more I read the more confused I become. 
I have my HDD Dock with PC Clone software so I can format the new hdd & load any stuff on to the new hdd before installing it back in to the laptop.
 
Things I am unclear on.
1, New hdd. will it need formatting if so what format.
 
2, Loads of stuff about drivers (mine field!) how what were.
 
3 Can I install ubuntu directly on to the new hdd.
 
Hope you all get the picture so to recap (brand new install no saved files or folders.) If some one can give me a quick run down bullet points on how to go about doing it that would be great.
 
Thanks Steve.

---

### Post by Smart Viking on 2010-05-19
1. You can format it to "ext4", while installing from a live cd.

3. Yes you can.

EDIT: I did not really understand question 2. :)

---

### Post by TeoBigusGeekus on 2010-05-19
1)Obtain ubuntu cd: download the iso from ubuntu.com and burn the image.
2)Restart pc and go into bios: search for device boot priority and make the cd as the primary.
3)Put ubuntu cd in and restart.
4)Ubuntu will load-choose install ubuntu
5)The installation procedure is straightforward (unless you have a 1 digit IQ) expect from the partitioning part.
6)In the partitioning, choose manual.
7)Create a 1GB partition and use it as swap.
8 )Create a 20GB partition and use it as root (mount point:/, file system ext4)
9)Create a 50GB partition and use it as home (mount point:/home, file system ext4)
10)Use the rest of the HD's space for Backup, torrents, etc. Create a partition for it and give as mount point:/media/disk (file system ext4)
11)Done!
12)Once in the Ubuntu Desktop, update Ubuntu (System->Administration->Update Manager)
13)System->Administration->Hardware drivers to see if you can enable restricted drivers for your system (for your graphics card for example)
14)Open terminal (Applications->Accessories->Terminal) and type
```
sudo apt-get install ubuntu-restricted-extras
```
This will install the necessary non-free codecs, flash pluggins, fonts, etc. that couldn't have been shipped with ubuntu due to terms' violations.

...And that's pretty much it!!!

---

### Post by philinux on 2010-05-19
@stevenjo,

2, Loads of stuff about drivers (mine field!) how what were.

The drivers for most hardware is included in the linux kernel, exception is graphics card. After install update the install using system>admin>update manager then look in system>admin>hardware drivers for any specific stuff like graphics card driver.

---

### Post by stevenjo on 2010-05-19
> **Smart Viking said:**
> 1. You can format it to "ext4", while installing from a live cd.
 
3. Yes you can.
 
EDIT: I did not really understand question 2. :)
 
 
Thanks for the quick reply ALL Phil answered question 2 :) 
 
Quick question about ext4 file format :confused: heard of fat, fat 32 and ntfs. Would I be able to view and share these files with a widows based pc, xbox360 etc or if anything should go wrong with the hdd again would I be able to retrieve any info with my other windows based pc or would it have to be a ubuntu based pc. :(
 
Also why is my profile pic not showing here. :(

---

