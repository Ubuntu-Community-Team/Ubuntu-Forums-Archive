---
title: "By accident deleted all my stuff..."
date: 2012-04-01
forum: General Help
---

### Post by voodoochild16 on 2012-04-01
Hey all, I did something by accident and I'm so #$%ing pissed that I didn't see it coming. I was trying to find my useless 160gb HDD to install ubuntu on, while using the ubuntu installer, and i noticed that one drive had 160gb's free on it so i clicked on it and thought it was the right one while not noticing it was my backup drive. So I formatted it and it began copying files from the ubuntu installer. I then clicked on Suspend because for some reason i didnt think it was the right thing to do. Then I rebooted into Windows 7 and noticed my 1TB backup drive was being asked by windows to be formatted... and then I felt like breaking a couple windows and came back to figure out what I could do to recover the files.

Well, i tried 4 or 5 different programs with no luck. Am I out of luck or is there a possible way of recovering my deleted files?.

---

### Post by -LynX- on 2012-04-01
have you take a look at this?

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by voodoochild16 on 2012-04-08
> **-LynX- said:**
> have you take a look at this?

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Thanks for the link. I am trying to do this from a Ubuntu 11.04 liveusb. 

I go to Terminal, type in **sudo swapoff -a**

then **sudo parted /dev/sdi2**

I get: 

[B]GNU Parted 2.3
Using /dev/sdi2
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)
[/B]

Then I go **rescue START END**

And I get: **Error: Invalid Number.**

If I type in: **print [devices|free|list,all|NUMBER]**
It says:

[B]Number  Start  End    Size   File system  Flags
 1      0.00B  983GB  983GB  ext4[/B]


I obviously found the directory of the drive from Gparted itself in the graphical program from the same liveusb. But I don't know which command to use to select the device number, how do I do this?.

---

### Post by codemaniac on 2012-04-08
> **voodoochild16 said:**
> [B]GNU Parted 2.3
Using /dev/sdi2
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)
[/B]



Seems like you are giving the wrong device number , i mean the hdd drive .Are you sure your drive is **/dev/sdi2** .

---

### Post by voodoochild16 on 2012-04-08
> **codemaniac said:**
> Seems like you are giving the wrong device number , i mean the hdd drive .Are you sure your drive is **/dev/sdi2** .

Yeah, because after typing sudo parted /dev/sdi2 and then typing 

[B]print [devices|free|list,all|NUMBER]

[/B]It says:[B]Number  Start  End    Size   File system  Flags
 1      0.00B  983GB  983GB  ext4[/B]

And that is the drive im trying to recover :/

---

### Post by sikander3786 on 2012-04-08
You can also try your luck with Photorec but the downside is while it will recover your data, it won't recover the file names:

[http://www.tuxgarage.com/2011/01/recover-deleted-data-using-photorec-in.html](http://www.tuxgarage.com/2011/01/recover-deleted-data-using-photorec-in.html)

And can you please post the output of:

```
sudo fdisk -l
```

---

### Post by voodoochild16 on 2012-04-08
> **sikander3786 said:**
> You can also try your luck with Photorec but the downside is while it will recover your data, it won't recover the file names:

[http://www.tuxgarage.com/2011/01/recover-deleted-data-using-photorec-in.html](http://www.tuxgarage.com/2011/01/recover-deleted-data-using-photorec-in.html)

And can you please post the output of:

```
sudo fdisk -l
```
I tried that as the beginning thing that I did in Terminal

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16db3fae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
33 heads, 12 sectors/track, 315771 cylinders
Units = cylinders of 396 * 512 = 202752 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x011e58f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           6         523      102400    7  HPFS/NTFS
/dev/sdb2             523      315765    62417920    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000250c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1275    10240000   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe94445db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121602   976762583+  ee  GPT
```

And then by typing

```
sudo swapoff -a

sudo parted /dev/sdh1

rescue START END
```

I got in return:

```
Error: /dev/sdh1: unrecognised disk label                                 
(parted)      
```

In the first long set of code it says "WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted."

Could this be the cause of the problem?. When I by accident formatted this drive, I was trying to install Ubuntu on it, how would Gparted not support it?.

---

### Post by sikander3786 on 2012-04-08
You can read about some interesting info on GPT in a recent thread here:

[http://ubuntuforums.org/showthread.php?t=1952953](http://ubuntuforums.org/showthread.php?t=1952953)

Regarding your issue, I don't have many pointers but you can wait for some other members to jump in.

---

