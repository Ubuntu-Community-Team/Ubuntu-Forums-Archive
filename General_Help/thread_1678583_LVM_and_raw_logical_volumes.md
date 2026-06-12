---
title: "LVM and raw logical volumes"
date: 2011-01-30
forum: General Help
---

### Post by rpaskudniak on 2011-01-30
Greetings.  An evil query for experts:

Last year I posted a question on how to get started with the Logical Volume Manager.  Nobody responded and, looking back on it, I don't blame y'all.  But now I have bitten the bullet, created 2 physical volumes (/dev/sda5, /dev/sda6), and two volume groups (vg-db01, db-vg02) and a total of 4 logical volumes of 1GB each.  I'll be creating more as I go along but I have one problem:

The logical volumes I created with lvcreate are all _Block_ devices.
```
$ find /dev/vg-db01   /dev/vg-db02 |xargs ls -lL
brw-rw---- 1 root disk 252, 0 2011-01-30 15:50 /dev/vg-db01/lvol-db001
brw-rw---- 1 root disk 252, 1 2011-01-30 15:55 /dev/vg-db01/lvol-db002
brw-rw---- 1 root disk 252, 2 2011-01-30 15:55 /dev/vg-db01/lvol-db003
brw-rw---- 1 root disk 252, 3 2011-01-30 16:03 /dev/vg-db02/lvol-db001
```
Note - I used the -L option in the ls command because the device files named are actually symlinks to the block special device files. For example:
```
$ ls -l /dev/vg-db01/lvol-db001
lrwxrwxrwx 1 root root 7 2011-01-30 15:50 /dev/vg-db01/lvol-db001 -> ../dm-0
```

I have mentioned in the past that I am an Informix DBA.  When I worked the LVM on HP-UX and AIX, whenever I created a new logical volume, it created a block device file, as above as well as a character device file.  In that case, the ls output would have  looked like:
```
**_c_**rw-rw---- 1 root disk 252, 0 2011-01-30 15:50 /dev/vg-db01/**_r_**lvol-db001
``` When I worked on a Red Had environment, I was not a system admin but the character raw volumes came up just the same.

I have not found any raw disk volumes post creation of the primary lvols.  I have been using find to look for [COLOR="Red"]-type c[/COLOR] files under /dev.

Perhaps I needed an option under vgcreate but I have not found that in the man pages.

Note: For the Informix-savvy out there: I know I don't really need to use raw volumes to bypass the cache (as Informix engines prefer); I know there is a mount option in /etc/fstab to sync all writes in a mounted file system.  But I am doing this as a training exercise and I need to know it.

How do I create the character disk device files to correspond to the block device files already created and in the future?  If I need to go back and recreate the volume groups I will do so.

Thanks much for help here.

---

### Post by srs5694 on 2011-01-30
> **rpaskudniak said:**
> The logical volumes I created with lvcreate are all _Block_ devices.
...
When I worked the LVM on HP-UX and AIX, whenever I created a new logical volume, it created a block device file, as above as well as a character device file.
...
When I worked on a Red Had environment, I was not a system admin but the character raw volumes came up just the same.

I've never heard of Linux creating character device files for LVM volumes. I've just checked on a CentOS system (CentOS being closely related to Red Hat) to which I have access, and it hasn't created any obvious character devices for its logical volumes. I suspect that you're not remembering your Red Hat experience correctly, although it's conceivable there's some obscure option for this somewhere. Googling on 'linux lvm "character device file"' produces a bunch of hits for HP-UX; the first page has nothing relevant to Linux. That makes me think there's no documentation out there on such a thing in Linux, and hence that it doesn't exist.

---

### Post by rpaskudniak on 2011-01-30
Eviler and eviler! z:twisted:

OK, I have found the command that would create a corresponding raw volume for a block device: The "raw" command.  In use, it would look like:
```
**[COLOR="Blue"]# raw /dev/raw/rvg01.lvol-db001 /dev/vg-db01/lvol-db001[/COLOR]**
Cannot open master raw device '/dev/raw/rawctl' (No such file or directory)
```
(Of course, I run that command as root - note the # shell prompt)

And therein lies my "eviler" designation!  I have found the correct command, yet my success is snatched away from me by this obscure error.  But, as some may already know on this forum, if I have been sufficiently annoyed into activity, I get popping! :popcorn:

In a post on the [informix-zone.com]("http://informix-zone.com"), I found [_the following tidbit_]("http://informix-zone.com/node/38"):
> Raw devices are character devices with major number 162. The first minor number (i.e. 0) is reserved as a control interface and is usually found at /dev/rawctl. The control device /dev/rawctl can be generated with the command

/sbin/modprobe raw
once I did this, I found the "device" /dev/raw/rawctl created.  I was then able to run this command:
```
# raw /dev/raw/raw01.db001 /dev/vg-db01/lvol-db001
```
I need to experiment a bit with naming conventions so that the fact that the corresponding block device is lvol001 on volume group vg-db01.  But I consider this a successful endeavor, although the name did not get created as I requested.  I tried to create /dev/raw/raw01.db001 and it created:
```
crw-rw---- 1 root disk 162, 1 2011-01-30 21:20 /dev/raw/raw1
```

That's OK; this is why symbolic links were created.

I have seldom been so satisfyingly annoyed! :guitar:

Now, what in tarnation is modprobe?  (Hmm.. The spell-checker des not like "tarnation"; Great balls of fire! Snuffy Smith should have been consulted!)  The man page says it all:
> program to add and remove modules from the Linux Kernel

So there is room for loss of devices upon reboot.  I'll find out soon and I will not consider this issue resolved until I reboot and find it all still in place.

Later...

---

### Post by rpaskudniak on 2011-01-30
SIGHHhhh...

I rebooted and /dev/raw was [SIZE="1"]*pfztztzt*[/SIZE] gone.

Not quite back to the drawing board but I need to find a way to keep that blessed module loaded permanently.  I think I need to have a close read at the modpobe man page.

Any additional help here - all you gurus, please?

Thanks much!

---

### Post by rpaskudniak on 2011-01-31
HMMmmm...
That same [_article in The Informix Zone_]("http://informix-zone.com/node/38") forum discusses creating a file named /etc/raw and a corresponding script /etc/init.d/raw.  The article, from 2006, assumes the file exists already and merely discusses extending it.  It also gives a sample script, which I already see has features I cannot use (like rc_reset commands).  It was written for Suse-Linux.  But I will shamelessly adapt what I can.

Since the file does not exists at all, I am inclined to extend this idea a great deal, with the following enhancements:

Instead of merely 2 fields for each line of /etc/raw (as the article discusses), use 5 fields:
raw1:vg-db01/lvol-db001:informix:informix:660

For this sample line, the start() function in /etc/init.d/raw would run the following commands:
```

[LIST]

[*]raw /dev/raw/raw1 /dev/vg-db01/lvol-db001
[*]chown informix:informix /dev/raw/raw1
[*]chmod 660 /dev/raw/raw1
[/LIST]

```
A list of more comprehensible symbolic links would be maintained in another directory.

This business of the raw devices vanishing upon reboot implies another requirement: I will need to script the creation of any new logical volume to maintain this convention:
[LIST=1]
[*]Create the lvol of specified size on the specified volume group
[*]Scan the list of (or directory) of existing raw devices in order to see the highest number, then generate next raw name 1 higher. (Use sort -n or, if using in a perl scipt, a sort function.)
[*]Run the [FONT="Courier New"]raw[/FONT] command to bind the newly named raw device to the newly created lvol
[*]Change the ownership to informix (or oracle or whatever)
[*]Set the permissions to 660 on the new raw device file
[*]Create a new entry in /etc/raw so that all the above will be repeated at the next run time.
[/LIST]
I suspect this is how I got my raw volumes in the Red Hat environment.  I recall there were times when, after a kernel upgrade, the machine would come up with no raw volumes, with the users squawking at the operations -> application programmers -> the DBAs -> the system admins. :mad:  Which reminds me to maintain a backup of both my new /etc/raw and /etc/init.d/raw.

OK, I suspect this is the path I will take.  I love scripting these kinds of things!

If someone has already invented this wheel, please step forward.  The article has some skeleton PHP code for the informix part of the deal but I'm asking about the raw script adapted for Ubuntu.

Comments? Contributions?

---

### Post by srs5694 on 2011-01-31
Interesting. I'd heard of raw devices, but didn't really know what they were. In any event, since they're distinct from LVM, it explains why my Google search turned up nothing.

Although using a startup script (I'd use /etc/rc.local, but a runlevel-specific script will work, too) to scan for existing logical volume device files and create the new raw device files will work, using udev might be a bit more elegant -- but I can't guarantee it would work. In case you don't know, udev manages creation of device files in /dev when kernel modules are loaded or when devices are detected. Thus, in principle, an appropriate udev rule will create the raw devices when the computer boots *or* when you create a new logical volume. I also thought to Google "linux udev raw devices" and came up with [this article,](http://www.remote-dba.net/t_rac_udev_rule_map_block_devices.htm) and [this post.](http://www.eggheadcafe.com/software/aspnet/36272225/proper-way-to-create-rawdevices-in-red-hat-enterprise-55.aspx) They should set you on the right track, although you might need to be more flexible in your device specifications. Googling "linux udev" turns up a ton of references on udev more generally, including [this one](http://www.linux-mag.com/id/3015) that I wrote for Linux Magazine a while back.

---

### Post by rpaskudniak on 2011-02-01
YIKES!

I have to learn too much in too short a time to use udev properly!  The articles apply more to other flavors of Linux, not to Ubuntu.  Hence, many of the directories mentioned in the articles do not exist on my Ubuntu box.  If I manually create them, they will likely go poof the next time I upgrade the kernel.

My method (which I think is a reverse-engineer of my former Red-Hat setup) is at least comprehensible to me, if potentially error-prone.

Y'know, after seeing your remarks and those of a couple of friends who know what I am up to, I am reminded of a Yiddish expression my Mom used to say: > If enough people tell you you're drunk, go to bed.  Since I installed IDS 11.70, which uses Direct Write (O_DIRECT?) I might save myself a few knots on the head by just using flat files.  If my next assignment should require the raw devices, I'll follow up on my scripts; I have the design already.  In the meantime, I'll go with the flow.  |:-[ (That emoticon is supposed to be a grumble.)

---

### Post by rpaskudniak on 2011-02-07
Just FYI for anyone interested in using LVM on Ubuntu:

I just came across this tutorial: [_How to Manage and Use LVM in Ubuntu_]("http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/") in a How-To-Geek mailing.  I suspect the person who posted in [_HowToGeek_]("http://www.howtogeek.com") saw this thread and decided the topic was appropriate.

Just letting y'all know about it.

BTW, it says nothing about raw volumes.  I gave up on that due to dwindling support for the facility with the Ubuntu world.

---

