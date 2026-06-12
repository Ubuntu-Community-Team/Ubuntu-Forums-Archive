---
title: "boot and hdd problems"
date: 2012-08-25
forum: General Help
---

### Post by bitbitbit on 2012-08-25
Hi all...

I'm new to ubuntu....and I got a 1TB hard disk with 2 GB RAM....

1) I right clicked home folder and found that the free space was only 10 GB...?!?! how come?! I would like to fully use the 1TB hard disk for all my music and photos....

2) I first installed Windows XP and then ubuntu...which ended up that everytime I turned on the computer, it askes me which OS i would like to use....is there any way to change such it boots from ubuntu without asking?

3) is 2GB RAM enough for ubuntu? i found that the system always lags...(i was just opening chrome+rhythm box+msn+software centre......)

thank you so much!! and sorry for asking dumb questions..... :(:(:(

---

### Post by Rexilion on 2012-08-25
1) I guess that the partition the installer created for you /home folder is probably also that big.

The output of:

```
df -m
```

will confirm that.

2) open: /etc/default/grub
Look for GRUB_DEFAULT=0
And if your Ubuntu installation is the second line, change it to:
GRUB_DEFAULT=1

And then execute as root:

```
update-grub
```

3) Opening software center is a pretty disk intensive task, Linux has some issue's under these workloads. Is that an explanation?

---

### Post by bitbitbit on 2012-08-25
1)

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       19G  8.0G   11G  44% /
udev            1.1G  4.1k  1.1G   1% /dev
tmpfs           419M  889k  418M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            1.1G  328k  1.1G   1% /run/shm
/dev/sda1       1.1T   15G  986G   2% /host


this is what it returns..... I don't really know what loop0, udev and tmpfs is....

2) erm....sorry, but how can I "open: /etc/default/grub"?? :-0 type that into the terminal? 

3) well, ok~ but is chrome compatible with linux?! for firefox would be better?...as chrome seems to clash quite often, esp on youtube.....


thank you so much!!!!

---

### Post by Rexilion on 2012-08-25
> **bitbitbit said:**
> 1)

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       19G  8.0G   11G  44% /
udev            1.1G  4.1k  1.1G   1% /dev
tmpfs           419M  889k  418M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            1.1G  328k  1.1G   1% /run/shm
/dev/sda1       1.1T   15G  986G   2% /host


this is what it returns..... I don't really know what loop0, udev and tmpfs is....

2) erm....sorry, but how can I "open: /etc/default/grub"?? :-0 type that into the terminal? 

3) well, ok~ but is chrome compatible with linux?! for firefox would be better?...as chrome seems to clash quite often, esp on youtube.....


thank you so much!!!!

1) /dev/loop0 ? For '/'. Is that a bad joke? Loop devices are most commonly used for read-only iso images (ie. CD's). What the heck did you do?  :lolflag:

All your free space is located at /host . So if you create a home directory under /host you get 986GB free space!!

2) Ehm...

```
sudo gnome-text-editor /etc/default/grub
```

3) Firefox has a start sequence that is also(!) used for stress testing the kernel's fsync performance . As it's called 'firefox fsync hell' :lolflag:. This is true, but after starting everything should be there.

I find chromium to be more lightweight, especially becuase it handles javascript much better thanks to it's V8(!) engine.

---

### Post by bitbitbit on 2012-08-25
1) T__T erm....i dunno what i really did.....
got a computer and install a windows (which is not genuine...), how ever end up clashing all the time (screen freezes with stripes....).....
so my friend suggest me with linux... and i install it over the windows.....

and that's all..... so what should i do now? is that loop0 thing serious?....lol
and how do i get the home directory to host?!@@

2)
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

grub_default=0 already on the first line...@@ so.....?

thank you so much for the help><!!

---

### Post by Rexilion on 2012-08-25
> **bitbitbit said:**
> 1) T__T erm....i dunno what i really did.....
got a computer and install a windows (which is not genuine...), how ever end up clashing all the time (screen freezes with stripes....).....
so my friend suggest me with linux... and i install it over the windows.....

and that's all..... so what should i do now? is that loop0 thing serious?....lol
and how do i get the home directory to host?!@@

2)
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

grub_default=0 already on the first line...@@ so.....?

thank you so much for the help><!!

1) Post the output of:

```
losetup -a
```

I'm genuinely curious about this one :D .

2) Like this:
0 corresponds to the first line you see when you start your computer (which is probably selected by default -> Windows 7)
1 corresponds the the second line you see when you start your computer (which is the default ubuntu kernel probably)
2 corresponds to the third line you see when you start your computer (which is the restore option for ubuntu)
n corresponds to the n-1 line you see when you start your computer

get it?

So, for example, if Ubuntu is really your second line when you start your computer. Then change this value from 0 to 1. Like this:

from:
```
GRUB_DEFAULT=0
```
to:
```
GRUB_DEFAULT=1
```

Then run the 'update-grub' command. Next time you reboot your computer, the second line will be highlighted by default.

---

### Post by black veils on 2012-08-25
there is something wrong with this situation. they said that they tried to install ubuntu over windows, because windows wasnt working, and now this is the result?

perhaps you should post the output of:```
sudo fdisk -l
```

better yet, do this [http://ubuntuforums.org/showpost.php?p=11136267&postcount=1](http://ubuntuforums.org/showpost.php?p=11136267&postcount=1)

and post the link you will be given, so we get a detailed view of your system situation.

---

### Post by bitbitbit on 2012-08-26
> **Rexilion said:**
> 1) Post the output of:

```
losetup -a
```

I'm genuinely curious about this one :D .

2) Like this:
0 corresponds to the first line you see when you start your computer (which is probably selected by default -> Windows 7)
1 corresponds the the second line you see when you start your computer (which is the default ubuntu kernel probably)
2 corresponds to the third line you see when you start your computer (which is the restore option for ubuntu)
n corresponds to the n-1 line you see when you start your computer

get it?

So, for example, if Ubuntu is really your second line when you start your computer. Then change this value from 0 to 1. Like this:

from:
```
GRUB_DEFAULT=0
```
to:
```
GRUB_DEFAULT=1
```

Then run the 'update-grub' command. Next time you reboot your computer, the second line will be highlighted by default.
1)...erm...the result is 
losetup: no permission to look at /dev/loop<N>

no permission?! how can I get permission?@@ there's only one users on this computer....


2) thanks for the detail explanation!! ^0^ but after i changed the grub file, and typed command update-grub....it returns this...seems something is missing?!@@
grub-mkconfig: You must run this as root

---

### Post by bitbitbit on 2012-08-26
> **black veils said:**
> there is something wrong with this situation. they said that they tried to install ubuntu over windows, because windows wasnt working, and now this is the result?

perhaps you should post the output of:```
sudo fdisk -l
```

better yet, do this [http://ubuntuforums.org/showpost.php?p=11136267&postcount=1](http://ubuntuforums.org/showpost.php?p=11136267&postcount=1)

and post the link you will be given, so we get a detailed view of your system situation.
for the command sudo fdisk -1, returns:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1e4a1e49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1953503999   976751968+   7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.



and also tried the boot repair app...
[http://paste.ubuntu.com/1168003/](http://paste.ubuntu.com/1168003/)


thanks!!

---

### Post by black veils on 2012-08-26
i dont know if you have UEFI or not. but i can tell you that you have windows installed still, you then have installed ubuntu using wubi, within your windows install.

seems like what you wanted to do is install only ubuntu over the whole disk ?

if yes, then this is what you need to do:

boot into your windows just to check in the disk manager if you have partition type **basic** or **dynamic**. if it is dynamic, you need to change the whole disk to basic.

then:
[http://ubuntuforums.org/showpost.php?p=12184305&postcount=2](http://ubuntuforums.org/showpost.php?p=12184305&postcount=2)

ignore the last link in that page^  what you need to do is just let the wizard do the partitioning for you, choose the erase entire disk option to use the whole disk.

---

### Post by Rexilion on 2012-08-26
> **bitbitbit said:**
> 1)...erm...the result is 
losetup: no permission to look at /dev/loop<N>

no permission?! how can I get permission?@@ there's only one users on this computer....


2) thanks for the detail explanation!! ^0^ but after i changed the grub file, and typed command update-grub....it returns this...seems something is missing?!@@
grub-mkconfig: You must run this as root

You need to prefix these commands with sudo as these commands require super user priviliges to do their work, like this:

```
sudo losetup -a
sudo update-grub
```

If you ever get an access denied error, run as root.

---

### Post by bitbitbit on 2012-08-26
> **Rexilion said:**
> You need to prefix these commands with sudo as these commands require super user priviliges to do their work, like this:

```
sudo losetup -a
sudo update-grub
```

If you ever get an access denied error, run as root.
GREAT!! thanks!!

for 1)
it returned...

/dev/loop0: [0801]:14792 (/host/ubuntu/disks/root.disk)

@@ dunno what it meant....

---

### Post by Rexilion on 2012-08-26
> **bitbitbit said:**
> GREAT!! thanks!!

for 1)
it returned...

/dev/loop0: [0801]:14792 (/host/ubuntu/disks/root.disk)

@@ dunno what it meant....

Is that an approved Ubuntu installation method? :shock:

---

### Post by bitbitbit on 2012-08-26
> **Rexilion said:**
> Is that an approved Ubuntu installation method? :shock:
approved? 0__0!!

erm....i just followed ubuntu's website....@@

should i "wash" my hdd and start it all over again?!?! @@ seems so many problems.....T__T

---

### Post by black veils on 2012-08-26
> **bitbitbit said:**
> approved? 0__0!!

erm....i just followed ubuntu's website....@@

should i "wash" my hdd and start it all over again?!?! @@ seems so many problems.....T__T

I guess you didn't see my post, you have Ubuntu installed through Windows, you should start again. 

I gave you clear information, so it won't be that difficult.

---

### Post by bitbitbit on 2012-08-26
> **black veils said:**
> I guess you didn't see my post, you have Ubuntu installed through Windows, you should start again. 

I gave you clear information, so it won't be that difficult.
OH 0__0 sorry for missing it...

let me try and see @@

thank you so much for help!! Rexilion and black veils !!~~ >v<

---

### Post by bitbitbit on 2012-09-21
> **black veils said:**
> I guess you didn't see my post, you have Ubuntu installed through Windows, you should start again. 

I gave you clear information, so it won't be that difficult.

sorry for getting back so late....but...I've downloaded latest version of ubuntu and checked md5sum in my terminal which prints:

xxxxx@ubuntu:~/Downloads$ md5sum ubuntu-12.04.1-desktop-i386.iso
e235b63c02644e219b7bf3668f479c9e  ubuntu-12.04.1-desktop-i386.iso

so now what should I do? burn the downloaded .iso to a usb and install ubuntu again?

btw, I can't find version 12.04.1 in the hashes listed here:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Many many thanks!!!

---

### Post by Bashing-om on 2012-09-22
your are doing good.
you are on the the right path.
you are asking the right questions.
md5 sum:[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Now if the md5sum checks:

my advise:
1. set bios to the cd as 1st boot priority.
2. Boot ubuntu => try ubuntu
     verify all works (graphics, web, printer ect ect)
3. install ubuntu:
    let the wizard install (as this is your first install), follow the prompts answering the 
          questions, at the install screen choose "use the entire disk" for ubuntu. 
           remember your user name and password ....your pass word is super important!
-------------
version 12.04 is the download version. In the installer look for the options to download the updates and 3rd party software ....check them.
The installer will do the updates to version 12.04.1, as well as updating all the other packages.

that is all there is to it ...soooo happy ubuntu'n <==BDQ

---

### Post by oldfred on 2012-09-22
With a 1TB drive it will create a massive / (root) partition and we have seen issues with some computers booting with large over 100GB) / partitions.

But then you have to manually partition and create a separate /home partition. You have to use Something Else to manually partition.

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited and if total less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB.  Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Erase entire drive and install:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Bashing-om on 2012-09-22
@ old fred ... Golly I stand corrected. You are a great teacher and source of inspiration.

 I continue to learn  new things daily  ==> BDQ

---

