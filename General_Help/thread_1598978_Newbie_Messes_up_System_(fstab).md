---
title: "Newbie Messes up System (fstab)"
date: 2010-10-17
forum: General Help
---

### Post by Quarkrad on 2010-10-17
Ubuntu 10.10. Rather than stay a newbie all my life I am gradually getting more adventurous, so occasionally things get messed up - normally I re-build but I would like to try and mend this one.  Rsync was taking a long time to copy from one of my drives to another so I decided to change the ownership of both drives, give them read/write access and to have them auto-mounted at boot (they are NTFS partitions).  Whether that was a good idea or not is long way back &#8211; I now have an issue (I believe) with my mtab and fstab files.  When I boot, just before I get the Desktop, I get this message:  **An error occurred while mounting 0   Press S to skip mounting or M for manual recovery.**  So I press S to access my Desktop.  If I launch Gparted and have a look at one of the partitions (sda5) and look at **Information**(Information for sda5) I get the following: 
[I]
File System: ntfs
Size:  272.03 giB

Path:  /dev/sda5
Status:  not mounted

Warning:
Error getting information about /dev/sda5: Input/output error

ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(5): Failed to check '/dev/sda5/ mount  state: Input/output error
Probably /etc/mtab is missing. It's too risky to continue.  You might try an another Linux distro.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.

The following list of software packages is required for ntfs file system support: ntfsprogs[/I]
 
**This is my fstab file:**

# /etc/fstab: static file system information.

#

# Use 'blkid -o value -s UUID' to print the universally unique identifier

# for a device; this may be used with UUID= as a more robust way to name

# devices that works even if disks are added and removed. See fstab(5).

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc  nodev,noexec,nosuid       0  0  

# / was on /dev/sda1 during installation

UUID=775f83e1-cbfa-4850-bf99-5913bf8c0085  /               ext4  errors=remount-ro         0  1  

# swap was on /dev/sda3 during installation

UUID=cfb8c8e7-8c83-4c84-827f-3ce65d539290  none            swap  sw                        0  0  

/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  

nls=iso8859-1,umask=000   0  0  

UUID=18187E06187DE64 /dev/sdb5 ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0

UUID=BA20F4F220F4B68B /dev/sda5 ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0

**This is my mtab file:**

/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0

proc /proc proc rw,noexec,nosuid,nodev 0 0

none /sys sysfs rw,noexec,nosuid,nodev 0 0

fusectl /sys/fs/fuse/connections fusectl rw 0 0

none /sys/kernel/debug debugfs rw 0 0

none /sys/kernel/security securityfs rw 0 0

none /dev devtmpfs rw,mode=0755 0 0

none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0

none /dev/shm tmpfs rw,nosuid,nodev 0 0

none /var/run tmpfs rw,nosuid,mode=0755 0 0

none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0

/dev/sda5 /dev/sda5 fuseblk rw,uid=1000,gid=1000,dmask=002,fmask=113 0 0

binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

gvfs-fuse-daemon /home/dad/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dad 0 0

Any help/advice appreciated.

---

### Post by yetiman64 on 2010-10-17
Can you post back here the results of,
```
sudo blkid | grep sda5
```This is to check the UUID in fstab for sda5. The resulting UUID from that command is what should be in fstab for sda5.

---

### Post by Quarkrad on 2010-10-17
It comes back with nothing(?)

dad@dadubuntu:~$ sudo blkid | grep sda5
[sudo] password for dad: 
dad@dadubuntu:~$ sudo su
root@dadubuntu:/home/dad# sudo blkid | grep sda5
root@dadubuntu:/home/dad#

---

### Post by Quarkrad on 2010-10-17
It is there

[I]dad@dadubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e93f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+  83  Linux
/dev/sda2            6375       12748    51199155    7  HPFS/NTFS
/dev/sda3           48260       48641     3068415   82  Linux swap / Solaris
/dev/sda4           12749       48259   285242077    f  W95 Ext'd (LBA)
/dev/sda5           12749       48259   285242076    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a4cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           1        8001    7  HPFS/NTFS
/dev/sdb2               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS[/I]

---

### Post by Morbius1 on 2010-10-17
The only thing I can think of is that the UUID is not correct. blkid should have shown you something but it's cache may be out of date:

Post the output of the following command instead:
```
sudo blkid -c /dev/null
```

---

### Post by yetiman64 on 2010-10-17
> **Quarkrad said:**
> It comes back with nothing(?)

dad@dadubuntu:~$ sudo blkid | grep sda5
[sudo] password for dad: 
dad@dadubuntu:~$ sudo su
root@dadubuntu:/home/dad# sudo blkid | grep sda5
root@dadubuntu:/home/dad#

Hmm, that's interesting try it with just "sudo blkid" (without the quotes) - this will give quite some output on some machines, which is why I tried to specify the particuar partition.

Just as a sample output example from my machine,> /dev/sda5: LABEL="Lucid64Rt" UUID="149c0b82-6646-47bb-9741-ac4ca76e7372" TYPE="ext4" this is an ext4 partition and the UUID is what I was looking for from your NTFS partition.

Edit: **use Morbius1's command**, I didn't remember the -c option when testing here with /dev/null.

---

### Post by Quarkrad on 2010-10-17
Output

/dev/sda1: UUID="775f83e1-cbfa-4850-bf99-5913bf8c0085" TYPE="ext4" 
/dev/sda2: UUID="782436E92436AA50" TYPE="ntfs" 
/dev/sda3: LABEL="swap" UUID="cfb8c8e7-8c83-4c84-827f-3ce65d539290" TYPE="swap" 
/dev/sdb1: UUID="B87C6DD17C6D8B48" TYPE="ntfs" 
/dev/sdb5: LABEL="backup" UUID="18187E06187DE364" TYPE="ntfs"

I note there is no /dev/sda5  -  which is the problem partition.  I can see sda5 in System/Admin/Disk Utility.  It says Device:  /dev/sda5   Mount Point:  mounted at /dev/sda5.  If I click on /dev/sda5 nautlius does not open - I get an error window - [I]Error: Error stating file '/dev/sda5': Input/output error
Please select another viewer and try again.[/I]

---

### Post by Morbius1 on 2010-10-17
> UUID=18187E06187DE64 /dev/sdb5 ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0

UUID=BA20F4F220F4B68B /dev/sda5 ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0You have no mount points.

UUID=18187E06187DE64 refers to a physical device
/dev/sdb5 also refers to a physical device
The system doesn't know what to mount the partition to.

My suggestion, for example on the first one:

Create a mount point
```
sudo mkdir /media/BackUp
```Then change the fstab line to this:
```
UUID=18187E06187DE64 /media/BackUp ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
```

---

### Post by Quarkrad on 2010-10-17
dad@dadubuntu:~$ sudo su
[sudo] password for dad: 
root@dadubuntu:/home/dad# sudo mkdir /media/BackUp
mkdir: cannot create directory `/media/BackUp': File exists


note:  I try and not have any captial letters - according to nautlus/gparted etc the label of /dev/sdb5 is **backup**

---

### Post by Morbius1 on 2010-10-17
If you're mounting it through Nautilus then unmount it first:
```
sudo umount /media/BackUp
```Then create the permanent mount point:
```
sudo mkdir /media/Backup
```Or create a completely different mountpoint:
```
sudo mkdir /media/MyBackup
```

---

### Post by Quarkrad on 2010-10-17
Ok - make dir and change fstab as you said.  When I reboot the sequence of screens/messages is:

[LIST]
[*]Grub screen (I choose Linux - I dual boot with XP)
[/LIST]
[LIST]
[*]Screen goes blank (loading Desktop)
[/LIST]
[LIST]
[*]Mauve screen (Ubuntu 10.10 screen) saying:
[/LIST]

[B]An error occurred while mounting 0
Press S to skip mounting or M for manual recovery[/B]

[LIST]
[*]I press S
[/LIST]

[LIST]
[*]Same mauve screen saying:
[/LIST]

[B]The disk driver for /media/Backup is not ready yet or not present.
Continue to wait: or Press S to skip mounting or M for manual recovery[/B]

---

### Post by oldos2er on 2010-10-17
What happens if you choose 'M'? Were the NTFS drives shut down cleanly?

---

### Post by Quarkrad on 2010-10-17
In both cases I am taken to black screen with a root command prompt  root@dadubuntu:#  There is some text above the command prompt - Filesystem checker or mount failed. A maintenance shell will now be started.

I guess Morbius1 was on the right tack - a mounting issue.

note.  When the Desktop is loaded - if I look in Nautilus then:

1.  **backup** is listed but not mounted (/dev/sdb5)
2.  no sign of **store**    (/dev/sda5)

It is a shame both partitions (on different HDs) have the same number (5) -  a little confusing.

---

### Post by Morbius1 on 2010-10-17
You need to put a # in front of every line in fstab the references an ntfs partition. .

Once you do that reboot into your system and post the output of:
```
cat /etc/fstab
```

---

### Post by Quarkrad on 2010-10-17
There has been a change - before I get Desktop I only a single (error) screen now - **An error occurred while mounting 0. Press S etc**.  When I press S I now go straight to the Desktop.  The output is:

dad@dadubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=775f83e1-cbfa-4850-bf99-5913bf8c0085  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda3 during installation
UUID=cfb8c8e7-8c83-4c84-827f-3ce65d539290  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
nls=iso8859-1,umask=000   0  0  
# UUID=18187E06187DE64 /media/backUp ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
# UUID=BA20F4F220F4B68B /dev/sda5 ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0

note:  the only fstab changes I made were to the last 2 lines - UUID=etc

---

### Post by Morbius1 on 2010-10-17
This one is right so remove the # sign from it:
>  # UUID=18187E06187DE64 /media/backUp ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0THis one is wrong because there is no such uuid , you have the wrong syntax, and it has no mountpoint:
> # UUID=BA20F4F220F4B68B /dev/sda5 ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
Which one of these do you want to automount:
> /dev/sda2: UUID="782436E92436AA50" TYPE="ntfs" 
/dev/sdb1: UUID="B87C6DD17C6D8B48" TYPE="ntfs"  

---

### Post by Quarkrad on 2010-10-17
OK,  I've removed the # from sdb5 (1818......) - I'm back to the two error screens.  Not mounting at 0 and /media/backup (sdb5).  At the moment I am not mounting anything according to nautilus.

To answer your question:

neither because sda2 is my winxp partition and sdb1 is a very small (MB) partition not in use.


The partitions I would like to automount are: 

sda1  775f83e1-cbfa-4850-bf99-5913bf8c0085  this is Ubuntu 10.10
sda5  BA20F4F220F4B68B   called **store**
sdb5  18187E06187DE364   called **backup**

Essentially /dev/sda5 **store** is my working workspace/storage on hd1 to which I back some folders to /dev/sdb5 **backup** which is on hd2. (I also back up my Ubuntu 'home' folder from /dev/sda1 to /dev/sdb5 **backup**.

---

### Post by matt_symes on 2010-10-17
Hi,

Cant mount 0

What is this line ?

nls=iso8859-1,umask=000   0  0  

A tip. If you want to change files, _always_ make a backup of the originals before.

Kind regards

---

### Post by Quarkrad on 2010-10-17
Sorry - I'm a newbie and struggling a bit.  Couldn't work out what you want me to do?  Especially the line nls......  Thanks for responding - I need your help.

---

### Post by Quarkrad on 2010-10-17
Apologies - it's the line in fstab.  I do not know what it means - and you are right, you would have thought all my years messing around (windows I'm afraid) I would have made a copy of the original fstab.  But ..... I'm here. I guess a rebuild will sort it but it would be nice to get it right.  I'm slowly trying to get my head around fstab etc.

---

### Post by matt_symes on 2010-10-17
Hi,

Don't rebuild. Lets try to fix this.

UUID=18187E06187DE64 /media/backUp ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0

sdb5 18187E06187DE364 called backup

If you look at the UUID between the two references closely you will see that one has DE64 and the other has DE364 as the last characters

Don't worry about making mistakes. The best way to learn.

These UUIDs are 16 alpha numeric characters long

Kind regards

---

### Post by matt_symes on 2010-10-17
Hi

Your new mount point will be backUp not backup. Follow _all_ the last posts and you should be fine.

If you are still having problems repost or message me.

Keep learning and you will be the one helping noobs here.

Kind regards

---

### Post by Quarkrad on 2010-10-18
I think I'm there - I can boot to my Desktop without the error screens although there is some text during boot which is on the screen too quick to see.  I can make out - error failed to allocate device.  

What I did: I tried various combination of expressing, in fstab, the partitions as /dev/xxx or /media/yyy.   The combination that works is:

UUID=18187E06187DE364 **/media/BackUp** ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
UUID=BA20F4F220F4B68B **/media/store** ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0

I also took out the line nls=iso8859-1,umask=000   0  0

Nautilus gives me what I am after - both store and backup are mounted.

Thank you for your help - I have learnt a little re: Linux.  (I am curious though what the flashing error is during the boot before Desktop).

---

### Post by Morbius1 on 2010-10-18
Now if someone could explain to me using monosyllabic words so that even I can understand it how this line mounts anything:

> UUID=BA20F4F220F4B68B **/media/store** ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0when blkid shows no such partition ( at least not with that UUID ) I would be grateful. 

Output of **sudo blkid -c /dev/null** as posted above:
/dev/sda1: UUID="775f83e1-cbfa-4850-bf99-5913bf8c0085" TYPE="ext4" 
/dev/sda2: UUID="782436E92436AA50" TYPE="ntfs" 
/dev/sda3: LABEL="swap" UUID="cfb8c8e7-8c83-4c84-827f-3ce65d539290" TYPE="swap" 
/dev/sdb1: UUID="B87C6DD17C6D8B48" TYPE="ntfs" 
/dev/sdb5: LABEL="backup" UUID="18187E06187DE364" TYPE="ntfs"

---

### Post by Quarkrad on 2010-10-18
I'm in the middle of a large data transfer from hd2 to hd1.  When it is finished I will run the **sudo blkid -c /dev/null** command again to compare to previous output.

---

### Post by matt_symes on 2010-10-18
Hi Morbius1,

Yeah your right. I just had a good chuckle.

At least 'cant mount 0' and 'backup' are sorted. Lets sort this guy out

Kind regards
[]("http://ubuntuforums.org/member.php?u=982144")

---

### Post by matt_symes on 2010-10-18
Hi,

I thought this link might be good for you

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Kind regards

---

### Post by Quarkrad on 2010-10-18
Here is my output of sudo blkid -c /dev/null

dad@dadubuntu:~$ sudo blkid -c /dev/null
[sudo] password for dad: 
[B]/dev/sda1: UUID="775f83e1-cbfa-4850-bf99-5913bf8c0085" TYPE="ext4" 
/dev/sda2: UUID="782436E92436AA50" TYPE="ntfs" 
/dev/sda3: LABEL="swap" UUID="cfb8c8e7-8c83-4c84-827f-3ce65d539290" TYPE="swap" 
/dev/sda5: LABEL="store" UUID="BA20F4F220F4B68B" TYPE="ntfs" 
/dev/sdb1: UUID="B87C6DD17C6D8B48" TYPE="ntfs" 
/dev/sdb5: LABEL="backup" UUID="18187E06187DE364" TYPE="ntfs"[/B] 

the only difference I can see the new line 
/dev/sda5: LABEL="store" UUID="BA20F4F220F4B68B" TYPE="ntfs"

hope this helps.

---

### Post by matt_symes on 2010-10-18
Hi

Unless i am going blind that looks fine to me. You can access BackUp and store correctly ?

BTW that text you could not quite see at bootup will be in the logs

Kind regards

---

### Post by Morbius1 on 2010-10-18
> **Quarkrad said:**
> 

hope this helps.
It actually does help in reaffirming to me how it is supposed to work. Not sure why blkid didn't report that before but .......

Thanks.

---

### Post by Quarkrad on 2010-10-18
Yes - all is fine, I can see both store and backup - they are both automounted at boot.  Thank you both for helping me on this one.  Appreciated.

---

