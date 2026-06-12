---
title: "RAID starting at md127 instead of md0"
date: 2011-05-22
forum: General Help
---

### Post by annagel on 2011-05-22
I have recently created a RAID 5 array under Ubuntu 11.04 and am having some trouble getting it to assemble correctly on system boot.  So far after every boot the array assembles correctly but in read-only mode at /dev/md127.  Stopping this array and running:

```
mdadm --assemble --scan
```

will correctly mount the array at /dev/md0.  My mdadm.conf file:

```
DEVICE partitions
ARRAY /dev/md/0 metadata=1.2 name=nagelnas:0 UUID=e4665ceb:15f8e4b6:b186d497:7d365254
```

detail of the array:

```

sudo mdadm --detail /dev/md0

/dev/md0:
        Version : 1.2
  Creation Time : Sun May 15 22:39:38 2011
     Raid Level : raid5
     Array Size : 5860544512 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1465136128 (1397.26 GiB 1500.30 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Sun May 22 09:52:09 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : nagelnas:0  (local to host nagelnas)
           UUID : e4665ceb:15f8e4b6:b186d497:7d365254
         Events : 18

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       5       8       64        4      active sync   /dev/sde


cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda[0] sde[5] sdd[3] sdc[2] sdb[1]
      5860544512 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>


```

examine of one of the disks in the array:

```

sudo mdadm --examine /dev/sda

/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e4665ceb:15f8e4b6:b186d497:7d365254
           Name : nagelnas:0  (local to host nagelnas)
  Creation Time : Sun May 15 22:39:38 2011
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 2930273007 (1397.26 GiB 1500.30 GB)
     Array Size : 11721089024 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 2930272256 (1397.26 GiB 1500.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 922f3fc5:b9078b42:86230bc3:b8abfc7e

    Update Time : Sun May 22 09:51:29 2011
       Checksum : 5274f4ec - correct
         Events : 18

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAAA ('A' == active, '.' == missing)

```


Any idea what I am doing wrong here?  Not the biggest deal in the world to assemble the array by hand but still something I want to have happen automatically.

Thanks, 
Andrew

---

### Post by annagel on 2011-05-22
Some additional information, after boot the status of the array is:

```
cat /proc/mdstat 

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid5 sdc[2] sdd[3] sde[5] sdb[1] sda[0]
      5860544512 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

```

---

### Post by gregmcc on 2011-05-23
I'm having exactly the same problems as you. I was running 10.10 with a RAID5 set as md0. Been working fine for ages. I upgraded to 11.04 and my raid is now appearing at md127. 

I have to stop the raid, run assemble which puts it back to md0 and I can then mount it.

---

### Post by technopagan on 2011-05-28
Thought I would post here to say that I had this same problem with ubuntu 11.04 -generic

With the -server kernel installed however, (11.04) works fine, for anyone who finds this thread.

---

### Post by justifiedandancient on 2011-06-06
I have exactly the same problem on Fedora 13:
uname -a
*** 2.6.34.8-68.fc13.x86_64 #1 SMP ***
Curiously, I tried changing /etc/fstab to mount /dev/md127 rather than what I originally had /dev/md0 and I still got the boot message:
Mounting local filesystems:  mount: special device /dev/md0 does not exist

---

### Post by YesWeCan on 2011-06-06
Hi all.
This seems to be a "feature" of the mdadm in the newest kernel. There was another thread with similar symptoms recently.
For reasons I do not yet understand, mdadm seems to invent an array device name out of thin air when there is a problem. This confuses everybody. md127 seems to be a common name it now chooses.

Two things seem to be important:

1) The ARRAY statement in mdadm.conf needs to be correct. I am not convinced the direct output of mdadm -Es is reliable anymore. Especially the name directive. Mine broke because I had a space in the name!
So I would try minimizing the specifiers in your ARRAY statements: all you normally need is device name and UUID:
```
ARRAY /dev/md0 UUID=e4665ceb:15f8e4b6:b186d497:7d365254
```
And there seems to be some change to do with /dev/md/* and /dev/md* which I don't yet understand.


2) You need to update initramfs so it contains your mdadm.conf settings during boot.
```
sudo update-initramfs -u
```

Try those and report back. :)

---

### Post by Steve Evans on 2011-06-10
Thank you! This was exactly the problem I was having and it's now all working wonderfully! :)

Steve

---

### Post by nasha on 2011-06-18
Yep, that's correct.

The new mdadm/kernel setup creates the default mdadm.conf file with --name=NAS:0 or equivalent.

When a --name parameter is set, a random (seems to always be 127) md device is created that actually symlinks to /dev/md/NAS:0 or equivalent.

Removing the name= from the mdadm.conf sets it back to normal

---

### Post by annagel on 2011-06-27
Thanks YesWeCan that worked for me as well...good thing I came back to this thread to check it out for some reason the auto-notify feature had stopped notifying me.

---

### Post by jonathanwalter on 2011-07-08
Yup. Worked for me too. Thanks!

---

### Post by Elendar on 2011-07-15
Worked for me too, thanks a lot

---

### Post by jaredheath on 2011-08-02
Worked for me as well.

This is a great "feature".  Just ate about 2 hours of my time.

---

### Post by vt_antik on 2011-08-10
> **YesWeCan said:**
> Hi all.
This seems to be a "feature" of the mdadm in the newest kernel. There was another thread with similar symptoms recently.
For reasons I do not yet understand, mdadm seems to invent an array device name out of thin air when there is a problem. This confuses everybody. md127 seems to be a common name it now chooses.

Two things seem to be important:

1) The ARRAY statement in mdadm.conf needs to be correct. I am not convinced the direct output of mdadm -Es is reliable anymore. Especially the name directive. Mine broke because I had a space in the name!
So I would try minimizing the specifiers in your ARRAY statements: all you normally need is device name and UUID:
```
ARRAY /dev/md0 UUID=e4665ceb:15f8e4b6:b186d497:7d365254
```
And there seems to be some change to do with /dev/md/* and /dev/md* which I don't yet understand.


2) You need to update initramfs so it contains your mdadm.conf settings during boot.
```
sudo update-initramfs -u
```

Try those and report back. :)

> **nasha said:**
> Yep, that's correct.

The new mdadm/kernel setup creates the default mdadm.conf file with --name=NAS:0 or equivalent.

When a --name parameter is set, a random (seems to always be 127) md device is created that actually symlinks to /dev/md/NAS:0 or equivalent.

Removing the name= from the mdadm.conf sets it back to normal

Good answers.  I dropped the name in my mdadm.conf and ran update-initramfs as described.  System is now where I want it to be.

---

### Post by dougnaka on 2011-08-17
> **nasha said:**
> Yep, that's correct.

The new mdadm/kernel setup creates the default mdadm.conf file with --name=NAS:0 or equivalent.

When a --name parameter is set, a random (seems to always be 127) md device is created that actually symlinks to /dev/md/NAS:0 or equivalent.

Removing the name= from the mdadm.conf sets it back to normal

FYI, if you are trying to use a large drive (2TB in my case) your problem is not simply mis-numbered RAID devices, it's the partition table on large drives are not the same. You have to use a GUID partition table (GPT) instead of the legacy MBR in all drives larger than 2TB.
Google "GUID partition table (GPT) grub linux howto"

---

### Post by Krupski on 2011-09-03
> **YesWeCan said:**
> Hi all.
This seems to be a "feature" of the mdadm in the newest kernel. There was another thread with similar symptoms recently.
For reasons I do not yet understand, mdadm seems to invent an array device name out of thin air when there is a problem. This confuses everybody. md127 seems to be a common name it now chooses.

Two things seem to be important:

1) The ARRAY statement in mdadm.conf needs to be correct. I am not convinced the direct output of mdadm -Es is reliable anymore. Especially the name directive. Mine broke because I had a space in the name!
So I would try minimizing the specifiers in your ARRAY statements: all you normally need is device name and UUID:
```
ARRAY /dev/md0 UUID=e4665ceb:15f8e4b6:b186d497:7d365254
```
And there seems to be some change to do with /dev/md/* and /dev/md* which I don't yet understand.


2) You need to update initramfs so it contains your mdadm.conf settings during boot.
```
sudo update-initramfs -u
```

Try those and report back. :)

Ran into the same trouble here with a RAID-6 array coming up as /dev/MD127.

Your tip worked! Thanks!!!

---

### Post by micahgalizia on 2011-09-13
Hi, I posted already in another thread, but I figure I'll post here too in case anyone ran into this. After fixing the UUID in mdadm.conf running update-initramfs outputs the following error:

```
mdadm: cannot open /dev/md/0: No such file or directory
```

However,I do have /dev/md0. I dont know what happened to mdadm so that it is expecting /dev/md/0 or why /dev/md0 is the device being created, but it seems to be keeping my array busted. If anyone knows how to solve this issue, I'd love to know.

Thanks in advance!

---

### Post by Krupski on 2011-09-17
> **micahgalizia said:**
> However,I do have /dev/md0. I dont know what happened to mdadm so that it is expecting /dev/md/0 or why /dev/md0 is the device being created, but it seems to be keeping my array busted. If anyone knows how to solve this issue, I'd love to know.

Thanks in advance!

I have never seen or heard of a /dev/md/0... it's always been /dev/md0.

FWIW.....

---

### Post by CrazyMike on 2011-11-12
> **micahgalizia said:**
> Hi, I posted already in another thread, but I figure I'll post here too in case anyone ran into this. After fixing the UUID in mdadm.conf running update-initramfs outputs the following error:

```
mdadm: cannot open /dev/md/0: No such file or directory
```

However,I do have /dev/md0. I dont know what happened to mdadm so that it is expecting /dev/md/0 or why /dev/md0 is the device being created, but it seems to be keeping my array busted. If anyone knows how to solve this issue, I'd love to know.

Thanks in advance!

I was having a similar issue with gparted saying something like "could not stat /dev/md/0" when my array is md0.  Also, the array was not getting found by nautilus/showing up in the Devices section for mounting.  



I'm not sure if this is the correct thing to do but I made the /dev/md directory then made a symbolic link to /dev/md0 by running 
```
sudo ln -s /dev/md0 /dev/md/0
```

Not the array shows up in gparted in the drop down/select window as /dev/md0 and it also shows in the devices window in Nautilus and is mountable by clicking on it.  Only quirk now is when you select /dev/md0 in the gparted drop down, the actual partition shows up as  /dev/md0p1.  

So far it seems to be working - aside from gparted showing a wonky name...

I'll keep playing with it...

---

### Post by CrazyMike on 2011-11-12
> **CrazyMike said:**
> Only quirk now is when you select /dev/md0 in the gparted drop down, the actual partition shows up as  /dev/md0p1.  


OK, nevermind /dev/md0p1 appears to be normal partition naming, so it appears I'm in good shape here...

---

### Post by YesWeCan on 2011-11-13
FYI I have done some more research on this and I wanted to share with you how I *think* mdadm with metadata 1.2 actually deals with device naming. I CANNOT FIND ANY COMPLETE DOCUMENTATION so this may not be a complete picture.

Each disk has a superblock that specifies a bunch of things but includes the array UUID and the array name.

The default is to assemble the array under the device names
/dev/md/<Name>  and /dev/mdN where N is made up but seems to start at 127 and count down. Note, two device files are created for one device.

It is as if at the /dev/md/ level it can use the name off disk but at the /dev/ level it has to use 'md' + a number.

However, if the disk Name happens to be a number (no text) then it uses this number at the /dev level too.

Ex1: If the on-disk Name=crazy8 the array device names will be /dev/md/crazy8 and /dev/md127

Ex2: If the on-disk Name=8 the array device names will be /dev/md/8 and /dev/md8

This had me very confused for a while.


Now, a device name in an ARRAY statement in mdadm.conf will override (partially) the disk name.

Ex3. ARRAY /dev/md2 UUID=ABCD... name=crazy8
/dev/md/2 and /dev/md2

Ex4. ARRAY /dev/md/pot UUID=ABCD... name=3
/dev/md/pot and /dev/md3

Notice that at the /dev level it will use a valid number from the name.


Following this? It gets worse! When you give an array a name that is just a number (no text) mdadm prefixes it with your hostname when it displays it.

Ex5. array name=88  and your hostname=tonys_pc
mdadm -Es will output
ARRAY /dev/md/88 ... name=tonys_pc:88

So I think "88" is all that is written to the disk superblocks but mdadm adds your hostname prefix to it when it displays it. So you are not seeing what is actually in the superblocks. But it DOES NOT use the hostname prefix name when allocating a device name. In this case the device names are
/dev/md/88 and /dev/md88



The bottom line for me is that it is essential to define an ARRAY statement in mdadm.conf to tell it what to call things so that it doesn't just go off and make names up that will confuse the heck out of you. :)

---

### Post by YesWeCan on 2011-11-13
> **CrazyMike said:**
> OK, nevermind /dev/md0p1 appears to be normal partition naming, so it appears I'm in good shape here...
Sort of normal. mdadm can create sub-partitions within a single md device. I have never used this "feature" and my brief experiments failed when trying to use normal tools to recognize the sub partitions. Anyhow, the naming style "mdxpy" is used to denote partition y of array x.

BTW when I want to have multiple partitions on a single md device I use LVM. Some folks avoid the issue by creating separate md devices for each partition they need.

---

### Post by nutznboltz on 2012-01-19
> **dougnaka said:**
> FYI, if you are trying to use a large drive (2TB in my case) your problem is not simply mis-numbered RAID devices, it's the partition table on large drives are not the same. You have to use a GUID partition table (GPT) instead of the legacy MBR in all drives larger than 2TB.
Google "GUID partition table (GPT) grub linux howto"


When I create a new md# of a GPT partition on 12.04 LTS I do not have an "ARRAY" entry in /etc/mdadm/mdadm.conf for that md# auto-generated for me.

If I run
```

sudo mdadm --detail --scan

```

the output line for "md127" is

ARRAY /dev/md/myhostname:2 metadata=1.2 name=myhostname:2 UUID=xx77xxf7:xx53xx89:acxxa4xx:xx33xxf9

but when I put 

ARRAY /dev/md2 metadata=1.2 UUID=xx77xxf7:xx53xx89:acxxa4xx:xx33xxf9

into /etc/mdadm/mdadm.conf the array still comes up as md127

If I go to the trouble of using
```

mdadm --stop /dev/md127
mdadm --assemble /dev/md2 /dev/sdc1 /dev/sdd1
```
before running the mdscan I still get:

ARRAY /dev/md2 metadata=1.2 name=myhostname:2 UUID=xx77xxf7:xx53xx89:acxxa4xx:xx33xxf9

Which doesn't help me a bit.

---

### Post by tpak on 2012-01-21
I suspect this is mostly related to the default device mapping changing from /dev/sdXX to /dev/xvdXXX

See my write up on page 5 over here:
[http://ubuntuforums.org/showthread.php?t=1468064&page=5](http://ubuntuforums.org/showthread.php?t=1468064&page=5)

simply try changing the device line in mdadm.conf, adjust for your devices obviously:

#DEVICE /dev/sdh[1-8]
DEVICE /dev/xvdh[1-8]

As I say in the other thread - I pulled my hair out today on this one and I think the device naming problem makes some sense. AS soon as I fed mdadm the correct device names all my problems cleared up - and the default output of  mdadm --detail --scan works fine in mdadm.conf

---

### Post by masuch on 2012-02-21
Thanks , yes we can. That solved my problem as well.

---

### Post by dtheurer on 2013-01-29
> **YesWeCan said:**
> Hi all.
This seems to be a "feature" of the mdadm in the newest kernel.
[...]
So I would try minimizing the specifiers in your ARRAY statements: all you normally need is device name and UUID:
```
ARRAY /dev/md0 UUID=e4665ceb:15f8e4b6:b186d497:7d365254
```And there seems to be some change to do with /dev/md/* and /dev/md* which I don't yet understand.

2) You need to update initramfs so it contains your mdadm.conf settings during boot.
```
sudo update-initramfs -u
```Try those and report back. :)
I was tearing my hair out on this one. Was migrating a RAID 1 array from a 10.04 box in which the system drive failed, so didn't have access to its mdadm.conf file. mdadm in 12.04 seems to "find" the array a little more easily than 10.04, but was also getting the md127 ("foreign") array crap happening.
What I did:
[COLOR=DarkRed]**Note:** The following was all done logged in as root.[/COLOR]

1) Get device names for array:```
fdisk -l
```2) In my case, my RAID 1 devices are sdb1 and sdc1, so I ran:```
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
mdadm --detail --scan
```3) Output from scan - with extraneous info removed - was used to update /etc/mdadm/mdadm.conf:```
ARRAY /dev/md0 UUID=af4*****:d39*****:998*****:82e*****
```4) Then I ran:```
update-initramfs -u
```and rebooted.
Problem solved.

Thanks, YesWeCan! :D
* Dirk*

---

### Post by unisubzero on 2013-06-12
Create !!!

Got it working too.

Thanks.

---

### Post by howefield on 2013-06-12
Old thread closed.

---

