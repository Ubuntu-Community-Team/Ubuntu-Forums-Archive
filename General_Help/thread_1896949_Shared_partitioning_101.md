---
title: "Shared partitioning 101"
date: 2011-12-18
forum: General Help
---

### Post by namutnubuk on 2011-12-18
k, i am having difficulties here, i have a dual boot setup on an nvidia stripping array and am trying to share a seperate stripping array consisting of 3tb's between W7 and kubuntu, ive tried EVERYTHING!!! and am losing whats left of my mind! ive tried formating the shared in ntfs through the windows installer, windows reads/writes and mounts, kubuntu sees it, but doesnt want to mount it, it is a GPT table, tried mounting through the text based installer of the release 11.10 as /windows, /home, /home/user, and as /home/Ron, just fails. tried rebuilding the array and formatting it to ext3 and mounting it as /home via the same installer but it gets stuck on creating an ext3 on partition xxxx..... and fails to mount /home while booting after installation, ive rebuilt the array and let it be(no partition tables, fs's, no mounting) and through konsole, created a gpt table on it, and then an ext3 fs, but it only shows the device in the dev/mapper!!! no partitions, ive tried mounting that and i ro access, wtf!!?? and i just see the seperate disks as empty in disk management(windows), as well as ext2fsd, thus not allowing me to access it via windows... ok, then i tried adding it to fstab with default settings, same results, ro...  ive also tried adding it to fstab as an ntfs-3g, defaults settings, i get a failed to moujnt error at boot....im getting a little annoyed. can someone please point me in the RIGHT direction???

---

### Post by namutnubuk on 2011-12-23
does a guy have to strap a bomb to his chest and scream around to get attention on this forum or what???

---

### Post by dcstar on 2011-12-23
> **namutnubuk said:**
> does a guy have to strap a bomb to his chest and scream around to get attention on this forum or what???

You **cannot** use crappy Windows filesystems for **any** Linux system folders like /home.

Linux systems require Linux filesystems.

---

### Post by namutnubuk on 2012-01-01
no kidding, was more of a last resort, and i think your missing the jest, i just want to mount this 3tb array i dont care what fs iit is as long as it works and i can r/w f/t it with both OS's, why doeswnt linux want to mount this ext3 on a gpt table as /home or / anything???? it sees the array but no partitions, example: in dev/mapper/ i have 
1.5tb array---------------------------------nvidia_xxxxxo--------------------               3.0tb array-----------nvidia_oxxxxx
Windows Partition-------------------------nvidia_xxxxxo1             
Windows partition-------------------------nvidia_xxxxxo2
Kubuntu------------------------------------nvidia_xxxxxo3----------------------------------------NO PARTITIONS!!!!
Swap---------------------------------------nvidia_xxxxxo4

even though i tried everything available, searched dozens of forums and fololowed a step by step guide on writing a gpt table and ext3 fs via konsole to a completely empty freshly built hw raid array, tried it through the gui kubuntu installer and the text based FAIL, i also gave gparted a shot FAIL.... my setup worked fine dividing the 1.5tb array up and having a shared ext3 partition that BOTH win7 and kubuntu could r/w f/t, so what, linux doesnt know how to handle a 3tb disk??? i know for sure the gpt table is written properly or i would not have been able to format an ntfs partition on it covering the whole disk...

anyone out there that knows how dto do this????

---

### Post by oldfred on 2012-01-01
I do not use RAID, but do have gpt partitions and shared partitions.

There may be some info here.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)

---

### Post by chipbuster on 2012-01-01
I would definitely use a RAID hardware controller if you can. If its in the software, a bad boot has the potential to make a lot of your data unrecoverable (until the array is re-indexed on another OS with the same software) whereas it'd take a hardware failure or a bad firmware flash to kill it.

---

### Post by namutnubuk on 2012-01-21
ya ive tried all these things, the fakeraidhowto guide is what i used to follow until the installer did all the work for you, yes hw raid is definately the way to go, but i even tried sw just for s&g, whats happening is when i tell the text based and the gui installer to format this 3tb array to ext3 and mount as /home it appears it isnt incorporated in /dev/mapper, all you can see is the disk, no partition, tried manually writing a gpt table and ext3 partition via konsole, then running the installer, no luck, what IS funny is that if i run gparted (command: sudo gparted /dev/mapper/nvidia_xxxxxx) and write a table and ext3 partition through that, then rerun it, it shows my new partition (nvidia_xxxxxx1), then i ran the following, dmraid -r, dmraid -ay, cd /dev/mapper, ls, and it listed the new partition as well, tried mounting it, and i got ro access. so i rebooted the beast, and the partition disappeared from dev/mapper, even tried the commands dmraid -r and dmraid -ay to re-initialize but got nothing, tried adding it to fstab and same results, i made sure ro was not a property. so what i think needs to happen is a permanent entry in dev/mapper for this device but have no idea how to go about this

---

