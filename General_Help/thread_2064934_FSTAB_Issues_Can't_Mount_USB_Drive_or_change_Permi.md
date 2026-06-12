---
title: "FSTAB Issues: Can't Mount USB Drive or change Permissions"
date: 2012-09-30
forum: General Help
---

### Post by neu5eeCh on 2012-09-30
OK. Wow. I haven't been this frustrated with Linux in a long time. Here's my situation:

My wife's HP Mini.

/dev/sda1 ext4
/dev/sda3 extended
/dev/sda5 linux-swap

sda = 15.7 GIB (an SSD)

And now for the problem partition/drive:

/dev/sdb1 ext4 1.88 GIB (a "permanent" USB)

Initially, sdb1 was fat32. I tried and tried and tried and tried to get her Read & Write access to the drive, but nothing doing. Linux refuses. (My wife has been unable to use this drive because something _**insists**_ that it must be root's and no one else's. So, I used the nuclear option. I deleted and reformatted the "drive" to ext4 (so I could change permissions). And yet, _**still**_, something refuses to cooperate. I tried through fstab, assigning the drive to user, uid=1000,gid=100 blah, blah, blah. None of these works. I just keep getting errors. Even when I try to change permissions, **as root**, the file manager refuses to give me the option. 

What the bleep!?! What do I need to do here? ](*,)

**EDIT:** Here, by the way, is the latest non-functioning entry in FSTAB:

/dev/sdb1  /media/Attic auto user,uid=1000,gid=100,dmask=027,fmask=137 0  0

I've also tried using the drive's actual UID instead of /deb/sdb1, but to no avail.

---

### Post by neu5eeCh on 2012-09-30
**Update: **I've gotten fstab to mount the drive.

/dev/sdb1  /media/Attic  ext4  rw,user,auto,exec 0   0

One problem is that I had accidentally typed ro instead of rw, but I don't know why [Ubuntu's own recommended]("http://askubuntu.com/questions/139739/change-permission-of-usb-drive") fstab entries didn't work.

Once that was fixed:

chown -R user_id:group_id     /media/Attic

Finally, finally fixed the problem. Another website had reversed the order of the chown command, putting the user_id:group_id _last_ instead of _before_ the file, like this:

chown -R [COLOR=Red]filename user_id:group_id[/COLOR].

So, I was partly the victim of bad online information.

---

### Post by mikodo on 2012-10-29
> **VTPoet said:**
> **Update: **I've gotten fstab to mount the drive.

/dev/sdb1  /media/Attic  ext4  rw,user,auto,exec 0   0

One problem is that I had accidentally typed ro instead of rw, but I don't know why [Ubuntu's own recommended]("http://askubuntu.com/questions/139739/change-permission-of-usb-drive") fstab entries didn't work.

Once that was fixed:

chown -R user_id:group_id     /media/Attic

Finally, finally fixed the problem. Another website had reversed the order of the chown command, putting the user_id:group_id _last_ instead of _before_ the file, like this:

chown -R [COLOR=Red]filename user_id:group_id[/COLOR].

So, I was partly the victim of bad online information.Were you following this guide:

[https://help.ubuntu.com/community/Fstab#Editing_fstab](https://help.ubuntu.com/community/Fstab#Editing_fstab)

If so, under: 

**File System Specific Examples**

is:
```

UUID=30fcb748-ad1e-4228-af2f-951e8e7b56df / ext3 defaults,errors=remount**-ro**,noatime 0 1Should it read:
remount-rw

```Should it be changed to :
```
UUID=30fcb748-ad1e-4228-af2f-951e8e7b56df / ext3 defaults,errors=remount**-rw**,noatime 0 1
```

---

### Post by neu5eeCh on 2012-10-29
Hi Mikodo,

I **did** use that site but I don't think that entry was the source of my error. The fstab entry you're offering to change involves a remount in case of error. In that example, perhaps, it's best that it be mounted as read only - but that all depends? If memory serves, the problem was that the "defaults" option, for some reason, didn't default to RW? - I had to specify RW.

---

### Post by mikodo on 2012-10-29
Oops.

Posted before reading your entry VTPoet

---

