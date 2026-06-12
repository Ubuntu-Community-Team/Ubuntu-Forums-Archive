---
title: "newbie needs help! grub errors 15, 17, 23 !!!!!"
date: 2009-07-03
forum: General Help
---

### Post by partynoparty on 2009-07-03
this is my first time with linux, and i'm not having much luck so far. i'm trying to install ubuntu 8.10 and having nothing but problems. 
after initially installing ubuntu, it would boot fine, but then i found that windows would no longer boot. they are installed on different partitions of the same drive. when i selected windows for booting, it came up with the error NTLDR is missing. 
at this point, i don't really know what i did. but things got worse. and now linux won't boot up either. all i get when i boot up the computer is a grub loading error 17. 
i searched around on the forums and i think i figured out what is wrong, but can't figure out how to go about fixing it. 
i went into "fdisk -l" and got some info back. i have three hard drives in my computer at the moment. two IDE and one SATA. one of the IDE has a windows installation that i don't really use anymore. the other IDE has the installation of windows that i normally use and ubuntu. the SATA is just for storage. fdisk gives me this info back

sda1 HPFS/NTFS

sdb1 HPFS/NTFS
sdb2 Linux
sdb3 Exteneded
sdb5 Linux Swap / Solaris

sdc1 HPFS/NTFS
sdc2 HPFS/NTFS

so i think i need to fix the grub parition order or reinstall grub or something. but i'm not exactly sure how. i tried "grub > root (hd0,1)" but it comes back with error 23. 

i need some help please!

---

### Post by nothingspecial on 2009-07-03
Have a look [[COLOR="Red"]here[/COLOR]]("http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems")

---

### Post by partynoparty on 2009-07-04
thanks much. that worked fairly easily. ubuntu is running fine now, as is the windows installation on my spare hard drive. however, i can't seem to boot into the windows installation that is on the hard drive with ubuntu. i receive a "missing or corrupt hal.dll" message. i googled it some, and i'm guessing it might be an issue with my boot.ini file pointing to the wrong partition. unfortunately, i don't know what the boot.ini file is supposed to look like. so my question is, how can i find out which partition is supposed to be specified in boot.ini?

---

