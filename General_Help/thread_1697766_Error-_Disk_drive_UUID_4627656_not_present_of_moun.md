---
title: "Error- Disk drive UUID 4627656 not present of mounting?"
date: 2011-03-01
forum: General Help
---

### Post by PDA1 on 2011-03-01
Periodically during boot up I get an error message which is something like this;

The Disk Drive UUID- (bunch of numbers and letters) is not present or not mounting.



Using blkid I have no drive with a UUID mentioned in the error message.

Any ideas what's wrong?

---

### Post by wt8008 on 2011-03-01
See if in your fstab file: /etc/fstab if there is a configuration for mounting that disk on boot. If there is, you can try commenting it out by putting a # in front of the line to see what effect it has.

---

### Post by seawolf167 on 2011-03-01
Write down the UUID the next time you see it, then read the contents of /etc/fstab and look for a match

```
sudo gedit /etc/fstab
```

You can comment out a line with the pound symbol '#', or simply backup /etc/fstab and delete that line all together.

---

### Post by PDA1 on 2011-03-02
This is what the fstab file says;


proc            /proc           proc    defaults        0       0
UUID=01XXXXXXf-d3b4-4cff-a20eXXCCVVB4e4b73ae /               ext4    errors=remount-ro 0       1
**UUID=048aa00c-e3de-47c5-847e-8b429a89d871** none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


I highlighted the UUID that appears as not mounting.

I'm running dual boot machine with XP and 10.04

Does this help explain anything?

---

### Post by AgentY on 2011-03-02
Did you create a swap drive on installation of Ubuntu? If so is the swap drive currently present/active?

---

### Post by PDA1 on 2011-03-02
Did you create a swap drive on installation of Ubuntu? 

I don't know.


If so is the swap drive currently present/active?

Not sure but here's what I get when I do "grep swap /etc/fstab"


Dav@Dav-desktop:~$ grep swap /etc/fstab
UUID=048aa99c-e3de-47c5-847e-9bd29a89d671 none            swap    sw              0       0


I also did the "swapon -s" command....why I don't know but I have an instruction sheet I made up of fancy Linux commands (that'll no doubt some day help me destroy my computer)

Dav@Dav-desktop:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/ramzswap0

---

### Post by seawolf167 on 2011-03-02
What happens if you run

```
sudo swapon -va
```

---

### Post by PDA1 on 2011-03-02
Here's what I get.....

Dav@Dav-desktop:~$ sudo swapon -va

swapon: cannot find the device for UUID=048aa99c-e3de-47c5-847e-9bd29a89d671

---

### Post by seawolf167 on 2011-03-02
First backup the /etc/fstab file

```
sudo cp /etc/fstab /etc/fstab.backup
```

Can you then edit /etc/fstab so the UUID is replaced with the /dev/sdXY value from fdisk

```
sudo fdisk -l
```find the swap partition, then replace the UUID in /etc/fstab so it looks like this

```
/dev/sdXY       none         swap    sw       0       0
```then try

```
sudo swapon -va
```again

---

### Post by PDA1 on 2011-03-02
Here's what I got......

Dav@Dav-desktop:~$ sudo swapon -va

swapon on /dev/sda6
swapon: /dev/sda6: found swap signature: version 1, page-size 4, same byte order
swapon: /dev/sda6: pagesize=4096, swapsize=3026870272, devsize=3026870784

---

### Post by seawolf167 on 2011-03-02
Looks like you're good to go, just run this last command to make sure the swap is active

```
free
```

---

### Post by PDA1 on 2011-03-02
Dav@Dav-desktop:~$ free

             total       used       free     shared    buffers     cached
Mem:       1009896     929588      80308          0       7704     184716
-/+ buffers/cache:     737168     272728
Swap:      3460864     519332    2941532

---

### Post by seawolf167 on 2011-03-02
> **PDA1 said:**
> Dav@Dav-desktop:~$ free

             total       used       free     shared    buffers     cached
Mem:       1009896     929588      80308          0       7704     184716
-/+ buffers/cache:     737168     272728
**Swap:      3460864     519332    2941532**

Looks good, let us know if there are still any problems

---

### Post by PDA1 on 2011-03-02
Thank you for the help.

I hope that solves it.

---

