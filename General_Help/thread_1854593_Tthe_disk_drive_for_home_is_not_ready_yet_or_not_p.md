---
title: "Tthe disk drive for /home is not ready yet or not present"
date: 2011-10-04
forum: General Help
---

### Post by MagikGimp on 2011-10-04
[I]OK, I'm going to keep this simple. Although I've read around about this problem I'd rather take it from the top if that's all right with everyone. So...
[/I]
Hi, at boot I get the error message "The disk drive for /home is not ready yet or not present", wait for it... what do I do please? Any help would be appreciated, thank you.

---

### Post by garvinrick4 on 2011-10-04
> Hi, at boot I get the error message "The disk drive for /home is not  ready yet or not present", wait for it... what do I do please? Any help  would be appreciated, thank you.Are you booting? If so.

Post output of:
```
cat /etc/fstab
```Just copy and paste.

##If you cannot boot where did you install /home to?

You can use a live cd (install cd or usb using Try UBuntu) and open a nautilus window (any window for home, docs, downloads) and on left will be
your file system for install open and go to file sytem to /etc to fstab. and copy and paste to this thread.

---

### Post by ajgreeny on 2011-10-04
From a live CD open nautilus file manager and double click the icons for your installed system partitions which should show in the left hand pane, then run the following three commands in terminal
```
sudo fdisk -l
cat /media/*ubuntu*/etc/fstab
sudo blkid
```
Where I show *ubuntu* in the second command you will need to use the correct name for the mountpoint of your ubuntu install which you can find once it is mounted by looking in nautilus.

---

### Post by MagikGimp on 2011-10-05
Thanks for your replies guys, I had a feeling this was going to be the next step.
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=50b815dd-f88f-47ce-be88-65123e027b2b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=9efc118d-6927-41cf-b287-47c3e67be0aa /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e63c4e16-cb89-4a4d-8e82-700862ad55fc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3fdb3fdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   162802709    81401323+   7  HPFS/NTFS/exFAT
/dev/sda2       162802771   488392064   162794647    5  Extended
/dev/sda5       162802773   320496749    78846988+  83  Linux
/dev/sda6       328675328   488386559    79855616   83  Linux
/dev/sda7       320499712   328673279     4086784   82  Linux swap / Solaris

Partition table entries are not in disk order

```(My swap partition is in between / (sda5) and what should be /home (sda6)).
Now then, as for blkid, the output from the live CD (apart from the dev/loop0 of course) is different from when I do it in the terminal at the log-in screen (I can boot but not enter X or whatever it's called); there's an extra line. I've merged both outputs together by hand just in case you need everything.
```

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="70283A0C2839D238" TYPE="ntfs" 
/dev/sda5: UUID="50b815dd-f88f-47ce-be88-65123e027b2b" TYPE="ext4" 
/dev/sda7: UUID="e63c4e16-cb89-4a4d-8e82-700862ad55fc" TYPE="swap" 
/dev/mapper/cryptswap1: UUID="40f88cf3-f3b7-4cb2-8ef3-4bcfb29d9f46" TYPE="swap"

```Also, could someone fix my typo in the topic's subject please? I can't do it myself. Thanks.

HOLD UP A MINUTE, I've just spotted something, have you?
```

/home was on /dev/sda7 during installation
/dev/sda7       320499712   328673279     4086784   82  Linux swap / Solaris

```Is this significant?

---

### Post by ajgreeny on 2011-10-05
Yes, I spotted that, and yes, it most definitely is significant.

Using the live CD/USB can you look into the partitions using nautilus and show us what is in them.  You will again need to mount the partitions (one by one in nautilus to avoid confusion) and then use the command ```
ls /media/*<home>*/
```  I always label my partitions using either gparted or tune2fs as it makes identification so much easier.  You can do it with command ```
sudo tune2fs -L **name** /dev/sdx#
``` from a live CD, and the partition will then always be mounted in /media/**name** where **name** is the label you gave it.  Where I show <home> you must use the /media/mountpoint you see in nautilus.

If we can be certain which is the real /home partition containing all your home files and folders, we should be able to edit fstab and all should be well.   If **/dev/sda6** really is your home, we need to either know the UUID or use /dev/sda6 in fstab instead, even if temporarily.  Try booting to recovery mode from the grub menu and go to a command line boot.  From there use the command sudo blkid again to try and find the UUID of /dev/sda6, then using ```
nano /etc/fstab
``` you will be able to either use the line ```
UUID=<figure-from-blkid> /home           ext3    defaults        0
```or ```
/dev/sda6 /home           ext3    defaults        0
```to replace the current line for /home in fstab.  Having done the edit use command mount -a to see if it works OK and report back here any error messages.

---

### Post by MagikGimp on 2011-10-05
Hi AJ,

Only my XP and / partitions are showing up in Nautilus hence the result of the blkid command (I presume).

Trying to label sda6 gives the error message "Bad magic number in super-block while trying to open /dev/sda6 Couldn't find valid filesystem superblock.

Indeed in gparted sda6 is listed as file system unknown and no UUID showing.

Again in root shell blkid shows no sda6 only Windows, / (on sda5) and swap (on sda7).

fstab hasn't changed from my last post. I don't think this is the problem and I think I may have thrown you by mentioning the comment. I should explain why I think this all might have happened:

I found I could not hibernate and read that my swap was not big enough. I shrunk /home with gparted after some difficulty realising I needed to leave about 3MiB at the end of the extended partition and increased my swap over where the beginning of /home was. I assumed this was OK to do as gparted would move the files no problem although I swore that I noticed that the used space amount had gone down which worried me. For a while everything was OK until I mistakenly installed an incorrect video driver and then my problem with /home occurred. I don't believe the two are related because I was able to remove the driver via the guest account but now I can't even log in with that. I also have a feeling I changed the UUID of my swap to make it work and that I may have mixed it up with /home (hence the comment) although this may not be the case as, like I said, things were OK for a short while. To be honest I'm not sure where things are; all I know for sure is all that stuff about changing partitions around AND that before Ubuntu I had Mageia and when I installed Ubuntu I didn't format /home (you'd think that would be OK what with all your files being there and all) and then having to delete my account and make a new one for Ubuntu. Sorry for the long paragraph but that's why I wanted to keep things simple to start with. Please read what I've said carefully as the clue we need might be in there.

So to summarise- fstab shows /home with a UUID and file-system but gparted does not although it does show a sda6. blkid does not show /home at all.

---

### Post by ajgreeny on 2011-10-06
Well, that has left me totally baffled, and I think I will have to bow out and leave the problem to those who are more able than I am to sort out an answer for you.

A few last questions:-
1.  Was the lost /home partition encrypted?  If so that is something I know nothing about.
2.  Is the partition table a standard msdos setup, and not the newer system for large disks over 2GB.  It appears to be a standard msdos partition table.
3.  Is there any way you can backup all the files etc on /home to another disk by using another OS, live or installed?  I assume not, but just want to double check this.

---

### Post by MagikGimp on 2011-10-06
Never mind AJ, the stranger things in computing often happen to me (and invariably often fix themselves too which is nice) but thanks for your input anyway. I'm tempted to just start again from scratch; it'll be a pain but like I said the setup is only a few days old.

When you ask if it's encrypted, I know that I checked the option to encrypt MY files but as for the whole partition, I don't think so. But anyway, I used gparted from my account so I would assume that it wouldn't have a problem or at the very least would have warned me if it did.

I have no idea what the setup is. I did see at one point things referred to as MSDOS1 etc. but I couldn't tell you where and if that's even accurate. The extended partition was made by Mageia if that's any help, I just reused the existing setup when installing Ubuntu (I formatted / but left swap and /home alone if you recall).

Not sure about backing up but I'm going to look into deleting /home but keeping / as all that is in /home really is settings and such whereas / has all the software I've downloaded.

Again, thanks for your help.

---

### Post by MagikGimp on 2011-10-06
OK, some development; I know what I need to do at least (I think). Booting from a live CD and using gparted I'm able to "format" the problem partition such that it's mountable in Nautilus. Inside is a folder called lost+found but I can't look in it due to not having the relevant permissions. So, this means I need to: 

[LIST=1]
[*]Gain access to that folder.
[*]Move the files out of the folder back into the root of that partition.
[*]Mark the partition as /home again.
[*]Edit fstab on / with the new UUID gparted allocates the partition on "formatting". I'll need the correct permissions to edit the file. My guess is also that gparted allocates a new UUID every time I format yes? In which case I'll need to do all of the above in one live CD session presumably.
[/LIST]
Easier said than done? Love to hear any suggestions.

---

### Post by ajgreeny on 2011-10-06
Assuming the encryption does not interfere with any of those operations, you should be able to do the file moving with ```
gksudo nautilus
```which will open nautilus with root permissions, and edit the fstab file with ```
gksudo gedit /etc/fstab
```both from the live CD if necessary.

If you are happy with the command line you can also do it booting into recovery mode from the grub menu.

---

### Post by MagikGimp on 2011-10-07
OK, so I've taken your advice and edited fstab and been able to browse the lost+found folder but there's nothing in there although there's still 1.37GB used disk space! Lord knows how I'd be able to retrieve that lost data.
I can boot without error messages now but can't log in. I'm going to have to create a new account with super-user privileges to delete mine and the guest account from the terminal now; wish me luck.

---

### Post by ssdeshpande on 2012-09-18
> **ajgreeny said:**
> From a live CD open nautilus file manager and double click the icons for your installed system partitions which should show in the left hand pane, then run the following three commands in terminal
```
sudo fdisk -l
cat /media/*ubuntu*/etc/fstab
sudo blkid
```Where I show *ubuntu* in the second command you will need to use the correct name for the mountpoint of your ubuntu install which you can find once it is mounted by looking in nautilus.

I have tried these instructions. What to do next solve the problem?

---

### Post by MagikGimp on 2012-09-18
Sorry but I was having this problem a long time ago. I can barely remember what it was all about but I'm pretty sure I just started again from scratch.

Although Unix OSes give a lot of precedence to the command line, my advice if you're inexperienced is to stay away from it as much as possible. This is 2012, Linux has come a long way in terms of complexity so typing in commands you're not familiar with often compounds the problem. Small changes are made which can make tracking the results difficult and often it is necessary to enter further commands afterwards. Sometimes these can be overlooked or it is not even realised that they are necessary meaning further problems will likely be encountered later along the line.
Taking time setting up your Linux installation carefully at the very beginning can save you a lot of bother and trying to stick to X Windows System interfaces wherever possible is my advice. Only when you learn what each command does fully should you be confident enough to use it.
Just my "two cents".

---

