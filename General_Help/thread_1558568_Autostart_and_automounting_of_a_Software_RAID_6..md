---
title: "Autostart and automounting of a Software RAID 6."
date: 2010-08-22
forum: General Help
---

### Post by CMDRSweeper on 2010-08-22
Hello, I am running a RAID 6 array via mdadm and I cannot make it autostart and automount at boot which is fairly imperative for a server config.
I am running the latest build of regular Ubuntu and not server, mostly because I have some other tasks for it that kind of requires a GUI, amongst that virtualization that I have so far working correctly.

Can anyone provide me with proper instructions on how to get the array running properly?
I found a few guides, added some things to the mdadm.conf which was supposed to be the end of it, however the array still doesn't start and let alone automount.

---

### Post by CMDRSweeper on 2010-08-22
Bump

---

### Post by CMDRSweeper on 2010-08-23
bump

---

### Post by Confucius! on 2010-08-23
Can you post the output of the commands below?
 
cat /proc/mdstat
 
cat /etc/mdadm/mdadm.conf
 
cat /etc/fstab

---

### Post by CMDRSweeper on 2010-08-23
Alright, what I got so far is this:

cat output from mdstat
```
sweeper@server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdf1[0] sda1[5] sdb1[4] sdc1[3] sdd1[2] sde1[1]
      5860542464 blocks super 1.2 level 6, 512k chunk, algorithm 2 [6/6] [UUUUUU]
      bitmap: 0/350 pages [0KB], 2048KB chunk

unused devices: <none>

```

cat output from mdadm.conf
```
sweeper@server:~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
"ARRAY /dev/md0 level=raid6 num-devices=6 metadata=01.02 name=:ICH9R Array UUID=5b2900f9:a845ac88:29902792:3320fd8a"

# This file was auto-generated on Thu, 19 Aug 2010 15:00:20 +0200
# by mkconf $Id$

```

cat output from fstab
```
sweeper@server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=35b62d71-fad8-4c06-814d-7020ed93ef8f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=31728932-013b-4548-8118-d3e06db441ef none            swap    sw              0       0

```

I included the initial command just to rule out some user errors on the input level.
Because I have to admit, I am a Linux freshman, and using Windows for this is not an option, it just sucks at software RAID.

---

### Post by rubylaser on 2010-08-23
Depending on the filesystem you've put on the mdadm array, you'll need to add an entry to /etc/fstab to actually mount the array.  Assuming you used ext4, it would look like this...

```
sudo mkdir /storage
```

```
sudo nano /etc/fstab
```
and paste this at the bottom...
```
/dev/md0	/storage	    ext4	defaults	0	0
```

Then, run this to mount the array at /storage

```
sudo mount -a
```

That should do it for you.

---

### Post by rubylaser on 2010-08-23
Also, if you chose to use ext4 you should also be aware of reserved space. By default ext4 will reserve 5% of the drives space, which only root is able to write to. This is done so a user cannot fill the drive and prevent critical daemons writing to it, but 5% of a large RAID array which isn’t going to be written to by critical daemons anyway, is a lot of wasted space. I chose to set the reserved space to 0%, using tune2fs:

```
sudo tune2fs -m 0 /dev/md0
```

---

### Post by CMDRSweeper on 2010-08-23
Thanks so far, it seems to automount now at least, but the RAID array does not autostart...
Which is also one of the problems I am having with it.
Thank you for the filesystem notice, yes the array is an ext4 and it consists of 6x 1.5Tb drives with the Intel ICH9R controller set to AHCI.

---

### Post by rubylaser on 2010-08-23
How is it automouting without the array being started? Or, are you starting the array by hand, then doing a mount -a afterwards?

Also, this is a longshot, but in your /etc/mdadm/mdadm.conf, the Array line doesn't need to be quoted.  This is what mine looks like.

```
DEVICE partitions
HOMEHOST <system>
MAILADDR root@localhost
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41
```

---

### Post by CMDRSweeper on 2010-08-23
Alright, I'll strip the quotes, presently when I restart Ubuntu halts saying it is waiting for /storage which should be the RAID array to mount, and it just halts there, forever, or until I hit S.
Once I get into Ubuntu I notice the array has not started, so that would be the logical cause of the mounting problem, it cannot mount an array that isn't started yet.

---

### Post by rubylaser on 2010-08-23
Okay, so, you're currently hitting S, and then mounting it by hand.  I was trying to figure out how it wasn't autostarting, but then was automouting itself.  The behavior you mention is doing what it should for an array that hasn't started.  How did you generate your mdadm.conf?

You can try it by hand if removing the quotes doesn't work...

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST <system>" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

---

### Post by Confucius! on 2010-08-23
Add the line below to your fstab. You will have to pick where it gets mounted to. The folder you are mounting it to must exist prior to it getting mount. So for example i will have to create a folder call RAID6 on user1 desktop before this can be mounted. This command mounts it on user1 desktop folder called RAID6. Change the comments if you like. The comments begain with the #. It is also assuming that it is a ext4 FileSystem. This is all one line. The reason it is not mounting is because you need to create the folder where you mounting it ontop of. Do not use /dev/md0 use the UUID!!!!!
 
 
#This is my RAID 6 array
UUID=5b2900f9:a845ac88:29902792:3320fd8a /home/user1/Desktop/RAID6 ext4 defaults 0 2

---

### Post by john newbuntu on 2010-08-23
If nothing helps, look into this post:
[http://ubuntuforums.org/showthread.php?t=1468064](http://ubuntuforums.org/showthread.php?t=1468064)

---

### Post by CMDRSweeper on 2010-08-23
Hmmm so far no luck, I am still greeted with the same thing when I reboot it.
The array was set up via GUI the so called disk Utility you find under the system -> Administration
I did build an array earlier on with the command line, same problem but this was done with virtual 4Gb harddrives in VMware.

I see that it seems to be a strange bug here with how things are handled, so I will investigate this, but one thing for sure, I am DDing an image of this HDD once I am done, I do not want this pain all over again in the future.

EDIT: However I wonder if this is relevant?
```
sweeper@server:~$ sudo mdadm --detail --scan
mdadm: metadata format 01.02 unknown, ignored.
mdadm: unrecognised word on ARRAY line: Array
ARRAY /dev/md0 level=raid6 num-devices=6 metadata=01.02 name=:ICH9R Array UUID=5b2900f9:a845ac88:29902792:3320fd8a

```

---

### Post by Confucius! on 2010-08-23
> **Confucius! said:**
> Add the line below to your fstab. You will have to pick where it gets mounted to. The folder you are mounting it to must exist prior to it getting mount. So for example i will have to create a folder call RAID6 on user1 desktop before this can be mounted. This command mounts it on user1 desktop folder called RAID6. Change the comments if you like. The comments begain with the #. It is also assuming that it is a ext4 FileSystem. This is all one line. The reason it is not mounting is because you need to create the folder where you mounting it ontop of. Do not use /dev/md0 use the UUID!!!!!
 
 
#This is my RAID 6 array
UUID=5b2900f9:a845ac88:29902792:3320fd8a /home/user1/Desktop/RAID6 ext4 defaults 0 2
 
 
This is now not going to work because you have deleted and recreate the array. You may have a new UUID for your array. Make sure the array is started and run the "sudo blkid" and post the output. Also post your /etc/mdadm/mdadm.conf. Using the GUI is a bad idea for creating arrays. It does not store the information in /etc/mdadm/mdadm.conf

---

### Post by CMDRSweeper on 2010-08-23
Hmmm, well I try the command even with sudo "mdadm --detail --scan >> /etc/mdadm/mdadm.conf"
And it spits back at me: "Permission denied"
Makes me wonder how that is possible, isn't Sudo supposed to be the all powerful Linux command for overriding such things?

Just for the record, I have no idea what I am doing, I am already pretty far out and trying things :P

---

### Post by Confucius! on 2010-08-23
Do sudo -s then run the command. This will give you root access so be carefull and type exit to exit.

---

### Post by CMDRSweeper on 2010-08-23
Things just keep getting more... Interesting.
```

sweeper@server:~$ sudo -s
[sudo] password for sweeper: 
root@server:~# mdadm --detail --scan >> /etc/mdadm/mdadm.conf
mdadm: metadata format 01.02 unknown, ignored.
mdadm: unrecognised word on ARRAY line: Array

```

---

### Post by Confucius! on 2010-08-23
Post the two commands below.
 
sudo blkid
 
cat /etc/mdadm/mdadm.conf

---

### Post by CMDRSweeper on 2010-08-24
Output from blkid
```
sweeper@server:~$ sudo blkid
[sudo] password for sweeper: 
/dev/sda1: UUID="5b2900f9-a845-ac88-2990-27923320fd8a" LABEL=":ICH9R Array" TYPE="linux_raid_member" 
/dev/sdc1: UUID="5b2900f9-a845-ac88-2990-27923320fd8a" LABEL=":ICH9R Array" TYPE="linux_raid_member" 
/dev/sde1: UUID="5b2900f9-a845-ac88-2990-27923320fd8a" LABEL=":ICH9R Array" TYPE="linux_raid_member" 
/dev/sdf1: UUID="5b2900f9-a845-ac88-2990-27923320fd8a" LABEL=":ICH9R Array" TYPE="linux_raid_member" 
/dev/sdb1: UUID="5b2900f9-a845-ac88-2990-27923320fd8a" LABEL=":ICH9R Array" TYPE="linux_raid_member" 
/dev/sdd1: UUID="5b2900f9-a845-ac88-2990-27923320fd8a" LABEL=":ICH9R Array" TYPE="linux_raid_member" 
/dev/sdg1: UUID="35b62d71-fad8-4c06-814d-7020ed93ef8f" TYPE="ext4" 
/dev/sdg5: UUID="31728932-013b-4548-8118-d3e06db441ef" TYPE="swap" 

```

And another cat from my mdadm.conf file after I ran that other command yesterday.
```
sweeper@server:~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid6 num-devices=6 metadata=01.02 name=:ICH9R Array UUID=76d66437-e3cb-4a3e-99a1-c03606ece4e5

# This file was auto-generated on Thu, 19 Aug 2010 15:00:20 +0200
# by mkconf $Id$

```

---

### Post by CMDRSweeper on 2010-08-24
Just a quick bump, as an added information judging from the date, the mdadm config was created when I installed the mdadm package.

---

### Post by CMDRSweeper on 2010-08-25
Bumping it again.

---

### Post by john newbuntu on 2010-08-25
Looks like you may have to modify your mdadm.conf to see if things work better.

Back up the current mdadm.conf.  Then do a "gksu gedit /etc/mdadm/mdadm.conf" and remove the word "Array" towards the middle of the line that begins with the word ARRAY.  Remove the phrase "metadata=01.02".  Also change the UUID to 5b2900f9-a845-ac88-2990-27923320fd8a from the current value that starts with 76d...  Save the file and run "sudo dpkg-reconfigure mdadm".

---

### Post by CMDRSweeper on 2010-08-26
Tried that, no change in behaviour at all yet.
It is starting to look like that tearing down the array and setting it back up again is becoming the only viable solution.

---

### Post by CMDRSweeper on 2010-08-26
Alright, let me recap, the array seems to start as it should, but it is not automounting.
However, using some of the previous posts in this thread, I MIGHT be able to solve that, I will update on what happens.

An update is, it now works.
Basically I did a rebuild of the mdadm.conf file using instructions provided by john Newbuntu 

And then Rubylaser's mounting instructions, the end result the array now starts at boot and mounts, and it works like a charm, now to secure my fort, I will DD it and secure it.

---

