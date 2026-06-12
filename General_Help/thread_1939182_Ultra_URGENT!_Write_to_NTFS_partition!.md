---
title: "Ultra URGENT! Write to NTFS partition!"
date: 2012-03-11
forum: General Help
---

### Post by mips on 2012-03-11
I'm posting in the cafe because it gets the most traffic.

Ubuntu 11.10 base with XFCE installed.

I urgently need to move 100GB of data to a NTFS partition but I cannot write to it.

I have ntfs-3g installed

---

### Post by TeoBigusGeekus on 2012-03-11
Try to change the ownership of its mount point
```
sudo chown -R yourusername: /media/mountpoint
```

---

### Post by matt_symes on 2012-03-11
Hi

Open a terminal and post back

```
mount
```

```
cat /etc/fstab
```

```
sudo blkid
```

How did you mount it ?

I expect this post will be moved.

You're right about traffic in this forum. 2 replies in a couple of minutes. The mods will kill you  mips for setting a precedent :)

Fine Hearty Sunday wishes to you both Teo and mips :)

Kind regards

---

### Post by TeoBigusGeekus on 2012-03-11
Alternatively, see this:
[http://ubuntuforums.org/showthread.php?p=11747147#post11747147]("http://ubuntuforums.org/showthread.php?p=11747147#post11747147")

PS: Hi Matt.

---

### Post by mips on 2012-03-11
```
xxxxx@obelix:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,user_xattr,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/xxxxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxxx)

```

```
xxxxx@obelix:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=ac1b4bea-685c-4aa6-81a9-c1b64f131688 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=7498ae35-460a-4e39-b74e-86952ab00792 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda4 during installation
UUID=ceac3c77-b4ae-47c1-9485-6d25193f07e1 none            swap    sw              0       0

```

```
xxxxx@obelix:~$ sudo blkid
[sudo] password for reon: 
/dev/sda1: UUID="A4AE5922AE58EE74" TYPE="ntfs" 
/dev/sda2: LABEL="root" UUID="ac1b4bea-685c-4aa6-81a9-c1b64f131688" TYPE="ext4" 
/dev/sda3: LABEL="home" UUID="7498ae35-460a-4e39-b74e-86952ab00792" TYPE="ext4" 
/dev/sda4: UUID="ceac3c77-b4ae-47c1-9485-6d25193f07e1" TYPE="swap" 
/dev/sdc1: LABEL="500GB_SG" UUID="c44d5744-bd62-4f48-b022-a606213326a1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: LABEL="PQSERVICE" UUID="DAA41C49A41C2B11" TYPE="ntfs" 
/dev/sdd2: LABEL="SYSTEM RESERVED" UUID="9C066D9B066D7764" TYPE="ntfs" 
**[COLOR="Red"]/dev/sdd3: LABEL="ACER" UUID="BE5E74F05E74A2B7" TYPE="ntfs"[/COLOR]** 
/dev/sdb1: LABEL="500GB_WD" UUID="4ab0dc57-61be-462e-a654-ccd5f1cf14c6" SEC_TYPE="ext2" TYPE="ext3" 
```

I need to write to /dev/sdd3 marked in red above.

---

### Post by mips on 2012-03-11
> **matt_symes said:**
> The mods will kill you  mips for setting a precedent :)

The data has to travel 300km shortly, window of opportunity is smaller than what nasa has to deal with.

---

### Post by matt_symes on 2012-03-11
Hi

Take a look at Teo's last post.

Kind regards

---

### Post by mips on 2012-03-11
> **TeoBigusGeekus said:**
> Alternatively, see this:
[http://ubuntuforums.org/showthread.php?p=11747147#post11747147]("http://ubuntuforums.org/showthread.php?p=11747147#post11747147")

PS: Hi Matt.

\\:D/ I could kiss you right now! Thanks a million it's busy copying!

Should take about an hour to copy the 100GB of data.

What a relief!

Now I don't care where the gods move this thread to :biggrin:

Thanks to all that assisted.

---

### Post by Elfy on 2012-03-11
A mod's seen it - still here from what I can see ... 

Once it's been dealt with I'll move it on though.

---

### Post by Elfy on 2012-03-11
> Now I don't care where the gods move this thread to K - I'll shift it along now then :)

---

### Post by mips on 2012-03-11
> **forestpiskie said:**
> A mod's seen it - still here from what I can see ... 

Once it's been dealt with I'll move it on though.

> **forestpiskie said:**
> K - I'll shift it along now then :)

Thanks forestpiskie, I really appreciate it. You have no idea how much I was sweating there [-o<

I suppose some days the 'gods' do smile down upon you ;)

---

### Post by Elfy on 2012-03-11
> **mips said:**
> Thanks forestpiskie, I really appreciate it. You have no idea how much I was sweating there [-o<

I suppose some days the 'gods' do smile down upon you ;)

Welcome mips :)

---

### Post by TeoBigusGeekus on 2012-03-11
Glad you've made it.

---

### Post by mips on 2012-03-11
> **TeoBigusGeekus said:**
> Glad you've made it.

Thanks again, the hard drive has reached it's destination so all is good. If you're ever in the neighbourhood I owe you beer or a beverage of your choice ;)

---

### Post by Elfy on 2012-03-11
off topic moved back to the cafe - thanks

---

### Post by matt_symes on 2012-03-11
> **forestpiskie said:**
> off topic moved back to the cafe - thanks

:popcorn:

---

### Post by mips on 2012-03-12
> **forestpiskie said:**
> off topic moved back to the cafe - thanks

Lol, it's come full circle :biggrin:

---

