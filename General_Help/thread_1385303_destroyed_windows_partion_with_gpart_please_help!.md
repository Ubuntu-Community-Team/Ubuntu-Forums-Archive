---
title: "destroyed windows partion with gpart please help!"
date: 2010-01-19
forum: General Help
---

### Post by kmsalex on 2010-01-19
OK so i burn a copy of 9.10 to a CD and started up the live desktop, when i got in i started up gpart. i desisted to give 40 GB to ubuntu i put in the numbers and came out with a 39.04 GB empty partion, so i toyed with it to try to get to 40 on the nose. this is the point where i should have walked away while i was ahead but i did't, i kept toying with it till i was almost there, but when i finally got it i realized i still had to finalized the changes so i hit the green check mark and let it run after 10 min's of gpart was reading my entire 180 gb partion which i had windows on. i grew in partion, and i remembered it was much quicker in the past when i partioned from inside the install so foolishly not knowing what i was doing i hit cancel. then my heart stopped when i saw the word unknown where it used to say ntfs. i relised i just destroy my windows install. i started to panic, because my backup of all my files where on another computer and guess what 3 days ago the hard drive died on it and i never got a chance to back up the stuff from this one to somewhere else. then i relised i had a 10 gb factory installed backup partion. so i restarted the machine and got nothing operating system not detected, and when i trying to got to the started up menu i didn't have the option to boot in recovery mode which i was expecting. but i had one last saving grace i upgraded from vista to 7 for free and still have the install disk, so i started up the install disc and selected recovery mode after trying automatic recovery and falling i tried restore from system image, it couldn't find the partion, as a last ditch effort i tryed system restore and as expected failed

i am at my wits end and have no idea what to do next short of wipe the drive and do a clean install, which i relay don't want to do because I'll lose all my data.
please any suggestions are greatly appreciated, i relay am hoping against hop there's something i can do as I'm in a bit of a panic over here as you can imagine.

---

### Post by michy99 on 2010-01-19
I think your best bet would be testdisk. It can find and repair deleted partitions. You can boot from the live cd, install testdisk from the repository and run it on your disk.

---

### Post by kmsalex on 2010-01-19
> **michy99 said:**
> I think your best bet would be testdisk. It can find and repair deleted partitions. You can boot from the live cd, install testdisk from the repository and run it on your disk.

i seam to be having troble figureing out how to install it, do you think you could walk me though it?

---

### Post by michy99 on 2010-01-19
The easiest way is to open a terminal (Applications->Accesories->Terminal) and enter this:```
sudo apt-get install testdisk
```

---

### Post by kmsalex on 2010-01-19
> **michy99 said:**
> The easiest way is to open a terminal (Applications->Accesories->Terminal) and enter this:```
sudo apt-get install testdisk
```

when i try that i get

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$

---

### Post by garvinrick4 on 2010-01-19
So I take it you did not make a 3 DVD image disc's of 7 to reinstall incase of disaster. You say a free upgrade it meant you did not get disc's? You have an image on its own partition in 7 that is completely different from the OS partition. Linux reads the partition as VISTA but it is not it is
the complete 7 image.

---

### Post by kmsalex on 2010-01-19
> **garvinrick4 said:**
> So I take it you did not make a 3 DVD image disc's of 7 to reinstall incase of disaster. You say a free upgrade it meant you did not get disc's? You have an image on its own partition in 7 that is completely different from the OS partition. Linux reads the partition as VISTA but it is not it is
the complete 7 image.

no when i said free upgrade i mean the free upgrade programe microsoft was offering, i got the computer on black friday cheap, big chach it came with vista. so i sent in for the upgrade disks. i now have the win 7 install disk and if i have to can do a clean install but the computer came with a restore partion but i can't figure out how to use it.

---

### Post by michy99 on 2010-01-19
Go to System->Administration->Software Sources and makes sure that the Universe repository is enabled.

---

### Post by kmsalex on 2010-01-19
> **michy99 said:**
> Go to System->Administration->Software Sources and makes sure that the Universe repository is enabled.

ok that seams to have worked

```
 ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ 


```

but where do i go from now?

---

### Post by michy99 on 2010-01-19
You need to run testdisk with root privileges so```
sudo testdisk
```

---

### Post by kmsalex on 2010-01-19
> **michy99 said:**
> You need to run testdisk with root privileges so```
sudo testdisk
```

after a while i eventualy get to
```
 estDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
[ MBR Code ]  Write TestDisk MBR code to first sector
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection






Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.



```

what should i do from there

i apologise for so many questions but i relay am a bit out of my depth here and don't have anyone else to help me.

---

### Post by garvinrick4 on 2010-01-19
Michy99 sounds like she or he has a plan in mind will bow out. Put a solved if it is cured please.

---

### Post by michy99 on 2010-01-19
Sorry, I had to go take care of a situation. You want to choose Analyse to see if it finds all your partitions.

---

### Post by kmsalex on 2010-01-19
its ok any your help is still greatly apreshated

```
 TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0  32 33 23872  31 24  383503609
P Linux                26354   1  1 28859 254 60   40258824
P HPFS - NTFS          28975  71 25 30400 232 40   22902784 [RECOVERY]





Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 196 GB / 182 GiB
 
```


the top one is the one i had windows on

---

### Post by michy99 on 2010-01-19
From there you should choose Quick Search.

---

### Post by kmsalex on 2010-01-19
there is no quick search option, i tryed selcting the frist partion and hiting enter and got this

```
 TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33 23872  31 24  383503609
 2 P Linux                26354   1  1 28859 254 60   40258824
 3 P HPFS - NTFS          28975  71 25 30400 232 40   22902784 [RECOVERY]






[  Quit  ]  [Deeper Search]  [ Write  ]
                          Try to find more partitions
 
```

---

### Post by michy99 on 2010-01-19
Ok, use the Deeper Search option.

---

### Post by kmsalex on 2010-01-19
it looks like it will take 3-4 hours its at 3% doing about a % every 3-4 mins, and thats all the partions on my drive so there should be anymore to be found?

---

### Post by michy99 on 2010-01-19
If there are no more partitions, then go ahead and stop it. Now you should select Write to write the partition table to the disk.

---

### Post by kmsalex on 2010-01-19
oh my god i am eternal in your dept. after i wrote the changes it said i had to restart before it would take effect so i did an just for the heck of it i tryed booting into windows and it worked!!! i cant begin to exprese how much i love you for this! i just wish i could repay you somehow, if you ever need help with anything on windows please don't hesitate to contact me. and trust me, from no one I'm back up everything!

but one last question is there any real point in keeping the backup partion
(as ovesly its of no help in an emergency!)

---

### Post by michy99 on 2010-01-19
I appreciate the offer, but I finally got rid of my XP partition about a month ago. I was only booting in to Windows every so often to make sure that it got updated. I eventually realized how dumb that was.

As to the backup partition, I would keep it unless you really need the space. Now that the partition table is fixed, it might work if you ever need it.

---

### Post by kmsalex on 2010-01-19
OK but if you ever reconsider feel free, again i relay do appreciate all of your help you've brought some of my most important files back from the brink of destruction, and for that i am very very grateful, and i think I'll take your advice on keeping the partion. and i think I'll be very very careful when i try installing ubuntu again.

regareds,
Alex

---

