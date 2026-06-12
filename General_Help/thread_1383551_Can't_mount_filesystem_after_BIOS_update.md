---
title: "Can't mount filesystem after BIOS update"
date: 2010-01-17
forum: General Help
---

### Post by blueshiftoverwatch on 2010-01-17
I just flashed/updated my BIOS using the MSI LiveUpdate4 utility under Windows 7. Everything worked the way it was supposted to as far as I can tell. Except that I can no longer boot up under Ubuntu. Windows XP and Windows 7 both boot up fine.

I get the error message:
> Mount of filesystem failed
A maintenance shell will now be started
CONTROL+D will terminate this shell and continue
Give root password for maintenance
I never set a root password under Ubuntu so I can't do that. It also said after failing to accept my user/sudo password something about running Fsck manually. So I put in the Ubuntu installation CD and am running it live. It comes with Fsck but there are quite a few options and I don't want to choose the wrong one and end up loosing data. I'm using Ext4 if that helps.

---

### Post by SuperSonic4 on 2010-01-17
Sounds more like an fstab problem - I'd have a look there first and comment out the UUID lines and add the paths (like /dev/sda1) in place of the UUID

For example, from my fstab ```
/dev/sdb1 / ext4 defaults 0 1
/dev/sdb2 /home ext4 defaults 0 1
/dev/sdb5 /var reiserfs defaults 0 1
/dev/sdb6 swap swap defaults 0 0

```

---

### Post by blueshiftoverwatch on 2010-01-17
> **SuperSonic4 said:**
> Sounds more like an fstab problem - I'd have a look there first and comment out the UUID lines and add the paths (like /dev/sda1) in place of the UUID

For example, from my fstab ```
/dev/sdb1 / ext4 defaults 0 1
/dev/sdb2 /home ext4 defaults 0 1
/dev/sdb5 /var reiserfs defaults 0 1
/dev/sdb6 swap swap defaults 0 0

```
So, if this is my /etc/fstab file:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4b2e0e7b-95ff-4a67-b8a6-4eff1b7ed0f9 /               ext4    errors=remount-ro 0 1
# /locmed was on /dev/sda8 during installation
UUID=ece78091-13d6-46e2-92e4-77e29326ce77 /locmed         ext4    defaults 0 2
# /virmac was on /dev/sda7 during installation
UUID=811ce18f-3c6c-40a1-871b-3c9a8d786eb4 /virmac         ext4    defaults 0 2
# swap was on /dev/sda6 during installation
UUID=0f1cde9d-9d89-4191-96a1-f260bd7e5bb3 none            swap    sw              0       0
/dev/scd0 /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0      0
```

What I would want to do is make it look something like this?

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / /dev/sda5 / ext4    errors=remount-ro 0 1
# /locmed /dev/sda8 /locmed ext4 defaults 0 2
# /virmac /dev/sda7 /virmac ext4 defaults        0       2
# swap /dev/sda6 none swap sw 0 0 /dev/scd0
/media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
This is all very confusing. The data seems to be randomly organized and I'm afraid that one space where there isn't supposed to be one will screw everything up. I guess this is what backups are for. But I'd like some more clarification before I continue.

---

### Post by oldfred on 2010-01-17
No the # are comments so they are not used.

UUID's are the preferred way as they are not supposed to change, but perhaps your BIOS changes caused a change. 

You can check UUIDs with

```
sudo blkid 
```

to see if they match.

otherwise.

entries should be like this:
old
# / was on /dev/sda5 during installation
UUID=4b2e0e7b-95ff-4a67-b8a6-4eff1b7ed0f9 /               ext4    errors=remount-ro 0 1

new
# / was on /dev/sda5 during installation
/dev/sda5 /               ext4    errors=remount-ro 0 1

---

### Post by blueshiftoverwatch on 2010-01-17
Thanks, I'm now booted up under Ubuntu. I saw it checking the partitions during boot process when you see the small white Ubuntu logo.

I wonder why upgrading my BIOS would cause a problem like this? Especially for Ubuntu when it didn't bother Windows XP or 7?

Is there any way to test if my swap space is working correctly? I tried to use the the 'sswap' tool in the secure-delete package to test it by seeing if I could write random data to it. But the 'swapoff -a' command didn't seem to work. As every time I typed 'sswap -f' to write over it, nothing happened.

---

