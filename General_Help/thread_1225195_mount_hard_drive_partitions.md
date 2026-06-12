---
title: "mount hard drive partitions"
date: 2009-07-28
forum: General Help
---

### Post by NovaAesa on 2009-07-28
Hi,

I have just installed a new hard drive (actually, it's been sitting in my computer for a week, but I've been waiting on a Molex to SATA power connector until today). It was showing up in gparted as sdb so I partitioned it in half (one 600GB partion, and one 400GB partion). Both partitions have been formatted to ext3.

I'm a bit stuck on what to do now though. I'm wanting to mount one partition to /home/ps/Media/ and the other to /home/ps/VMImages/

Does anyone know what I should be doing to get these to mount on startup?

---

### Post by DaithiF on 2009-07-28
Hi,
take a look at this guide:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

from step 4. (optional) or 5. onward

cheers
d

---

### Post by frunns on 2009-07-28
Can't check what that guide says here at work, but I'd recommend Pysdm, easy GUI for editing fstab, so the partitions are mounted where you want at boot.

---

### Post by NovaAesa on 2009-07-28
Okay, I used a combination of that guide and pysdm to get it happening. I have a few concerns though. Both partitions say that they already have data on them. One has 17.5GB used, and the other 29.5GB used. They only folders they have inside them are lost+found, which are empty. Any clues what is going on with that?

---

### Post by Zenze on 2009-07-28
Formatting the drive uses space on the drive, so it might just be that.

---

### Post by DaithiF on 2009-07-28
I would guess if you run a command to see disk usage for the new mount points you WON'T see usage of 17.5 and 29.5 gigs.
```
du -sh /mount/point
```

Are you perhaps inferring that 17.5 and 29.5 gigs have been used from the amount of free space reported?  ie. the free space is less than you expected by those amounts?

If thats the case then the explanation is contained in the link from earlier, the section entitled
**[SIZE=3]Modify Reserved Space (Optional)[/SIZE]**

[https://help.ubuntu.com/community/InstallingANewHardDrive#Modify%20Reserved%20Space%20(Optional)]("https://help.ubuntu.com/community/InstallingANewHardDrive#Modify%20Reserved%20Space%20%28Optional%29")

basically by default 5% space is reserved.  You can reduce this if you want for a data partition (but not a system partition).

cheers
d

---

### Post by munky99999 on 2009-07-28
```
sudo mkdir /home/ps/Media/
```

```
sudo gedit /etc/fstab

  /dev/sdb1    /home/ps/Media   ext3    defaults     0        2
```
```

sudo mount -a
```

that should do it. Obviously change sdb1 to whatever partition it's seen as.

doing ```
mount
```

will tell you all the drives that are around.

---

### Post by NovaAesa on 2009-07-28
Yep, the issue was with the reserve space. All fixed up now using
```
sudo tune2fs -m 0.5 /dev/sdb1
```
Thanks all!

---

