---
title: "I/o errors on healthy drive?"
date: 2011-03-22
forum: General Help
---

### Post by Atamisk on 2011-03-22
Hello, 

Whenever i do a cold startup (as opposed to a restart), i end up with a repeatable i/o error after roughly 5 minutes. This completely renders the system useless, and i'm talking to myself about raising elephants. I can _always_ restart right after the incident, and it _always_ starts up and i can use linux without incident for _days_. 

What would do this? Is there a log i can peruse that might offer insight?

Also, this is a new sympton as of the last 2 kernel updates.

Actual solution: 

See [This launchpad bug.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267913") solution is about halfway down

---

### Post by markp1989 on 2011-03-22
> **Atamisk said:**
> Hello, 

Whenever i do a cold startup (as opposed to a restart), i end up with a repeatable i/o error after roughly 5 minutes. This completely renders the system useless, and i'm talking to myself about raising elephants. I can _always_ restart right after the incident, and it _always_ starts up and i can use linux without incident for _days_. 

What would do this? Is there a log i can peruse that might offer insight?

Also, this is a new sympton as of the last 2 kernel updates.

try looking at the disk utilit program  ( under system > administration) 

then look at the smart data for your drive see what it says

---

### Post by Atamisk on 2011-03-22
Drive is healthy, with no realloc'd sectors or other maladies. i've run tests up to "Extensive" on it in the recent past. HDD is less than 6 months old.

---

### Post by matt_symes on 2011-03-22
Hi

> What would do this? Is there a log i can peruse that might offer insight?

The logs i would look at are 

```
/var/log/syslog
/var/log/messages
/var/log/kern.log
```

They will be your best bet i would imagine.

If you can get to a terminal or console just after it happens type (or leave it running in a terminal)

```
dmesg | tail 
```

Kind regards

---

### Post by Atamisk on 2011-03-22
Okay, so the drive checks clean, and so do the error logs. none of them  so much as mention an EXT4 error. 

But, if i happen  to be working a terminal when the error strikes, i'm treated to a  read-only filesystem error in the terminal. This tells me that the drive  is remounting itself for seemingly no reason. i ran e2fsck -f from a  recovery CD, and got: 

```

e2fsck 1.41.12 (17-May-2010)
Checking for bad blocks (read-only test): done                                
Desktop: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

Desktop: ***** FILE SYSTEM WAS MODIFIED *****
Desktop: 398048/19202048 files (0.3% non-contiguous), 20458530/76800000 blocks

```i'm so damn frustrated with this!

---

### Post by matt_symes on 2011-03-22
Hi

> This tells me that the drive is remounting itself for seemingly no reason.

You can check that by typing mount after it happens and checking the options of the drive. I would certainly double check that as it's being remounted as read only ?

```
mount
```

/dev/sda5 on / type ext4 (rw,errors=remount-ro)

Nothing in dmesg ? Nothing in /var/log/messages ?

What does your fstab look like BTW ?

Kind regards

---

### Post by tgalati4 on 2011-03-22
Your drive probably has some bad blocks.  The statement:

Checking for bad blocks (read-only test): done                                
Desktop: Updating bad block inode.

means that the file system check found a bad block, relocated the data, and put the ID# of the bad block into a list so that it won't be used in the future.

Open a terminal and run:

sudo badblocks /dev/sda

If you get a list of bad blocks then it may be time to retire or return the drive.

---

### Post by Atamisk on 2011-03-22
Nope, the badblocks inode is just fine. 

I believe there was an error in my fstab. Instead of reading

defaults,errors=remount-ro

It just read

errors=remount-ro

Ever since i changed that, no issues. 

Also, the bad block inode is empty.

---

### Post by matt_symes on 2011-03-22
Hi

> **tgalati4 said:**
> Your drive probably has some bad blocks.  The statement:

Checking for bad blocks (read-only test): done                                
Desktop: Updating bad block inode.

means that the file system check found a bad block, relocated the data, and put the ID# of the bad block into a list so that it won't be used in the future.

Open a terminal and run:

sudo badblocks /dev/sda

If you get a list of bad blocks then it may be time to retire or return the drive.

That's interesting. Maybe run smartctl on the disc as well then to get a comprehensive read out of the disks SMART status. The command line can give more info than disk utility.

```
sudo smartctl -t long /dev/sda
sudo smartctl -a /dev/sda
```

Kind regards

---

### Post by Atamisk on 2011-03-23
Still experiencing symptoms. However, i did something crazy and set errors=continue, in hopes of catching the error in a log somehow. Hopefully i don't nuke the filesystem.

---

### Post by matt_symes on 2011-03-23
Hi

The drive is not doing something stupid like powering down for some reason is it ?

After it gives you trouble open a terminal and type

```
sudo hdparm -C /dev/sda
```

Kind regards

---

### Post by matt_symes on 2011-03-24
Hi

What is the exact make and model of the drive ? 

I know some drives have had firmware issues and as there is nothing in the logs to indicate what is happening i am wondering if that is maybe the issue.

Kind regards

---

### Post by Atamisk on 2011-03-24
[IMG]http://i11.photobucket.com/albums/a187/Usagi190/Info.png[/IMG]

If it helps.

---

### Post by Atamisk on 2011-03-26
Still symptomatic, logs show nothing.

Attempting to see if the drive is powering down after a hardware-set time. Can't find anywhere that says it would though.

---

### Post by dcstar on 2011-03-26
> **Atamisk said:**
> Still symptomatic, logs show nothing.

Attempting to see if the drive is powering down after a hardware-set time. Can't find anywhere that says it would though.

And that is a WD "Green" drive looking at the info you have given.

These drives spin up more slowly than normal drives to save on power, put a delay in your BIOS to allow the drives to get up to speed before the boot procedure commences - a few seconds may be all that is needed. It also could be that the kernel timings have changed recently so the drive also tries to shut down (to save power) too often, and the restart timings aren't working correctly.

I have read that these drives spin down automatically after 8 seconds, and the Linux kernel has a default 10 second drive poll interval so these drives may be continually unloading and reloading.

The following commands may be able to change this:

```
sudo hdparm -S 3 /dev/sda
sudo hdparm -B 255 /dev/sda
```

If they work, put them into the /etc/hdparm.com file.

---

### Post by Atamisk on 2011-03-26
I think it worked! I'll edit the title tomorrow after some thorough testing, but i seem to be in the clear. Many thanks to the ones that helped!

I Owe y'all!

-Aaron

EDIT: Yup, Solved!!

---

