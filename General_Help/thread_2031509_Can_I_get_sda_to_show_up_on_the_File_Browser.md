---
title: "Can I get sda to show up on the File Browser?"
date: 2012-07-22
forum: General Help
---

### Post by ksanger on 2012-07-22
I've been running Ubuntu 12.04 for about 2 months and I'ld like to look at my disk usage but I can not find sda under the file browser.  The browser opens to the Home folder.  Under devices I can right click on sdb and see its properties.  But sda is not shown.

Under the magic button, installed apps, disk usage, I get the total space of both drives.  I suppose I could subtract them in my head; unless I had more than two drives.

Disk Utility shows sda1 and sdb1 and their total capacity.

---

### Post by Bucky Ball on 2012-07-22
Install Gparted if it wasn't installed with 12.04 LTS. That is the 'official' Ubuntu partition manager. You will see it all. Lets you mount/unmount, resize, format, etc ... gives full usage stats. ;)

There are other tools for this but I don't need to use 'em so can't comment.

---

### Post by ksanger on 2012-07-22
On my system GParted gives me used space for sda1 but not sdb1?  Seems hokey that I can get Properties by right clicking on sdb1 through the File Manager and then have to find another application to look at sda1?  Then GParted gives me information on sda1 but not sdb1?

---

### Post by Bucky Ball on 2012-07-22
Have you clicked on the drop-down list in the top right of the Gparted GUI which says 'sda'? sdb should be there.

---

### Post by ksanger on 2012-07-22
Yes GParted says that sdb1 is unallocated, Size 298.09 GiB, Used --- Unused ---.
File shows my files on sdb1.  

Bizarre behavior if you ask me.  I know I have files on sdb1.  I can edit them and view them and listen to music.

---

### Post by Bucky Ball on 2012-07-22
Yea, just not mounting by the sound of it. Try this, just paste the commands into a terminal one at a time, hitting return after each:

```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```

This should create a mount point in /media for sdb1 then mount it there. Does it now mount and appear in a file browser??? If not, what error are you getting (copy and paste it back here)?

If it mounts okay we can make it permanent by changing the fstab or, if this an NTFS filesystem, install 'ntfs-3g' (and 'ntfs-config' from memory) and run that will show you NTFS partitions, let you choose which to mount at boot, and rewrites the fstab for you. ;)

---

### Post by ksanger on 2012-07-23
Hmmm.  I did this for sda and now it shows up under File browser and I can see its properties.  Just have to figure out how to make it permanent.  But I did notice that the find command sees the new sda as a replicate of another mounted disk?  And I can not figure out how or where I mounted sdb.  This is what I've done.

Under media I had an sdb folder.  So I created an sda folder and mounted sda1.

Now File browser shows sda and give me its free and unused space.  But I'm not the owner so I can not do anything with it like create a new folder at the root directory.  Which is okay.

Then I searched for fstab
cd \
sudo find . -name fstab -print

which returned
***find: File system loop detected; `./media/sda' is part of the same file system loop as `.'.***
./etc/fstab
./lib/init/fstab
./usr/share/doc/mount/examples/fstab

It looks like the OS knows that sda is the same as something else.

./lib/init/fstab has commands to add to /etc/fstab to add mount points.  But I don't see sdb?  Here is my /etc/fstab file.

more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=528d96e3-f118-4b37-bb69-cf13c088e7b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=96c934d8-432f-4ede-9f26-981e2c3ed1ea none            swap    sw              0       0

Don't see sdb and do not remember the instructions I used to mount that.

Did find instructions to use blkd so I used them to find out the UUID of sdb1.
sudo blkid
/dev/sda1: UUID="528d96e3-f118-4b37-bb69-cf13c088e7b7" TYPE="ext4" 
/dev/sda5: UUID="96c934d8-432f-4ede-9f26-981e2c3ed1ea" TYPE="swap" 
/dev/sdb1: LABEL="sdb" UUID="21ac52c2-6813-4c94-8204-2b609c93fe0e" TYPE="ext4" 

That explains the strings seen in fstab.  But sdb doesn't show up.

---

### Post by Bucky Ball on 2012-07-23
Try mounting sdb1 at boot like so:

```
# / **was on /dev/sda1 during installation**
UUID=528d96e3-f118-4b37-bb69-cf13c088e7b7 / ext4 errors=remount-ro 0 1
```

The part I have in bold shows that the partition numbers have been moved around and that is perhaps where the confusion comes from. The line above is for sda1, right? So, to backup fstab:

```
sudo cp /etc/fstab /etc/fstab.backup
```

Then:
```

sudo nano /etc/fstab
```

Go the the bottom of the file and add this line, same as the entry for sda1, but changing the UUID to that of sdb1, like so:

```
# comment line for description of entry
UUID=21ac52c2-6813-4c94-8204-2b609c93fe0e / ext4 errors=remount-ro 0 1
```

Ctl+X then 'y' to save and exit. Reboot. Is it mounted? ;)

PS: If you screw your fstab:

```
sudo cp /etc/fstab.backup /etc/fstab
```

... gives you the original fstab to screw up all over again!

---

### Post by ksanger on 2012-07-23
Before I try this, how do I figure out how sdb1 is currently getting mounted?  If I don't disable that won't it be mounted twice like I have sda now?

---

### Post by Bucky Ball on 2012-07-23
By the looks of your fstab it is not getting mounted at boot so the only other way it would be mounted is manually, I guess. ;)

You could boot and check in /mnt and /media. That would be the only two places it would be gettting mounted. It should also be in /dev/sdb1 but that is the block device, not really a mounted drive as such.

---

### Post by BLTicklemonster on 2012-07-28
From here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

open terminal and enter sudo blkid

/dev/sda1: UUID="8aac5db5-393e-41a1-8762-f1c61e6176fd" TYPE="reiserfs"

then sudo gedit /etc/fstab

now edit the lines

UUID=8aac5db5-393e-41a1-8762-f1c61e6176fd /media/sda1 reiserfs 0 0

for each instance other than the first two in fstab which are the first two in blkid (root and swap)

rebooted, and all partitions mounted

---

### Post by ksanger on 2012-07-28
I'm sorry but I'm not familiar with fstab.

for sudo blkid I get:
/dev/sda1: UUID="528d96e3-f118-4b37-bb69-cf13c088e7b7" TYPE="ext4" 
/dev/sda5: UUID="96c934d8-432f-4ede-9f26-981e2c3ed1ea" TYPE="swap" 
/dev/sdb1: LABEL="sdb" UUID="21ac52c2-6813-4c94-8204-2b609c93fe0e" TYPE="ext4" 

In fstab I currently have:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=528d96e3-f118-4b37-bb69-cf13c088e7b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=96c934d8-432f-4ede-9f26-981e2c3ed1ea none            swap    sw              0       0

My questions are:
1)  I know I need to use the UUID for my drives and not the one you've specified which must be for yours.
2)  I don't see sdb in fstab.  However sdb1 is mounted as sdb on my system when I boot.  If I add sdb to fstab then will it be mounted twice using two differing methods?
3)  I do not see sda or sda1 in the File program.  I do see sdb in the File program.  I like seeing sdb in the File program and being able to see its free space and used space under properties.  If I add sdb in fstab and figure out how to disable the method that is used to currently mount it.  Won't it disapear from the File application at which point I would not be able to examine either drive's properties using the File application?
4)  In your instructions you state edit the lines *UUID=myDriveNumber /media/sda1 reiserfs 0 0* for every instance except the first two.  As you can see in fstab my drive is listed once.  I assume this means that sda1 is also being mounted using another method just like sdb1?  Since sdb shows up in the File application, and sda does not, and both sda and sdb are not in fstab, then may I assume there are three methods of mounting drives upon boot up?  Two of which have not been discussed here.  Maybe I need a new post title "How many different ways may one mount a drive when booting Ubunut 12.04?".  Which ones to use and what is the difference?
5) man fstab does not describe what *reiserfs *does.


I hate to be anal.  I have found other methods to see the used and unused space on sda1; that I probably will not remember when I need too.  Plus the methods don't show both drives so that requires remembering how to access each one.   Remembering how to do unique esoteric Linux commands is not high on my list of things to do in my lifetime.  Ideally the computer is a tool that is easy to use; not consuming too much human memory.  I suppose I could buy an Apple but I'm afraid that I'ld be starting over again...

---

### Post by BLTicklemonster on 2012-07-28
> **ksanger said:**
> I'm sorry but I'm not familiar with fstab.

for sudo blkid I get:
/dev/sda1: UUID="528d96e3-f118-4b37-bb69-cf13c088e7b7" TYPE="ext4" 
/dev/sda5: UUID="96c934d8-432f-4ede-9f26-981e2c3ed1ea" TYPE="swap" 
/dev/sdb1: LABEL="sdb" UUID="21ac52c2-6813-4c94-8204-2b609c93fe0e" TYPE="ext4" 

In fstab I currently have:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=528d96e3-f118-4b37-bb69-cf13c088e7b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=96c934d8-432f-4ede-9f26-981e2c3ed1ea none            swap    sw              0       0

My questions are:
1)  I know I need to use the UUID for my drives and not the one you've specified which must be for yours.
2)  I don't see sdb in fstab.  However sdb1 is mounted as sdb on my system when I boot.  If I add sdb to fstab then will it be mounted twice using two differing methods?
3)  I do not see sda or sda1 in the File program.  I do see sdb in the File program.  I like seeing sdb in the File program and being able to see its free space and used space under properties.  If I add sdb in fstab and figure out how to disable the method that is used to currently mount it.  Won't it disapear from the File application at which point I would not be able to examine either drive's properties using the File application?
4)  In your instructions you state edit the lines *UUID=myDriveNumber /media/sda1 reiserfs 0 0* for every instance except the first two.  As you can see in fstab my drive is listed once.  I assume this means that sda1 is also being mounted using another method just like sdb1?  Since sdb shows up in the File application, and sda does not, and both sda and sdb are not in fstab, then may I assume there are three methods of mounting drives upon boot up?  Two of which have not been discussed here.  Maybe I need a new post title "How many different ways may one mount a drive when booting Ubunut 12.04?".  Which ones to use and what is the difference?
5) man fstab does not describe what *reiserfs *does.


I hate to be anal.  I have found other methods to see the used and unused space on sda1; that I probably will not remember when I need too.  Plus the methods don't show both drives so that requires remembering how to access each one.   Remembering how to do unique esoteric Linux commands is not high on my list of things to do in my lifetime.  Ideally the computer is a tool that is easy to use; not consuming too much human memory.  I suppose I could buy an Apple but I'm afraid that I'ld be starting over again...

Okay, so look at the UUID information from blkid and fstab and compare.

You will see the first two entries from blkid match fstab, but the third entry is missing from fstab.

Looking at fstab, the first entry is your root directory, which is where your operating system is set. That is what the "/" means. / = Root.

The second one is your swap file. 

What you want to do is automatically load the third one that blkid shows, right?

Just take the information from blkid that isn't in fstab (that would be the third line) and enter it into fstab following the format used in fstab.

(Reiserfs is a file system just like ext4 is. I use reiserfs, and looking at your information, you use ext4)

Anyway, take this information:
```
/dev/sdb1: LABEL="sdb" UUID="21ac52c2-6813-4c94-8204-2b609c93fe0e" TYPE="ext4"
``` 
and turn it around to this:
```
UUID=21ac52c2-6813-4c94-8204-2b609c93fe0e /media/sdb1 ext4 0 0
```

and add it to your fstab like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=528d96e3-f118-4b37-bb69-cf13c088e7b7 /           ext4 0 1
# swap was on /dev/sda5 during installation
UUID=96c934d8-432f-4ede-9f26-981e2c3ed1ea none            swap    sw              0       0
UUID=21ac52c2-6813-4c94-8204-2b609c93fe0e /media/sdb1 ext4 0 0
```

That's what I would do and did, and it corrected years of problems I had from using the same drives over and over in different configurations.

**If you are the least bit uncomfortable with this though, then don't.**

---

### Post by BLTicklemonster on 2012-07-29
Did you give it a go? Did it help?

---

