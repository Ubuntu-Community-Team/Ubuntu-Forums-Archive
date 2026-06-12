---
title: "vfat Mounting issues"
date: 2012-02-12
forum: General Help
---

### Post by jamedfor on 2012-02-12
Hey guys,

semi-Ubuntu noob here.  I have ubuntu, along with a vfat shared partition and an XP partition, installed on my HP laptop.  I'm having trouble getting full rw access to the vfat partition from ubuntu.  I tried chmod and similar commands, as well as a few programs like the default disc manager, pysdm, and MountManager.  They all appear to give me access, but I still cant write.  

I can write on the shared partition fine from XP.

My problems seemed to start when I tried to make the drive mount on boot, which is still rather important to me.

Let me know if there is already a thread on this, I didn't see one...

I appreciate any help!

-John

---

### Post by Vishnu V on 2012-02-12
fstab  may contain only read access 
try this
/dev/sdaX /mountpoint  vfat rw,username	0	0

---

### Post by jamedfor on 2012-02-12
Thanks for the post Vishnu.  I assume you mean to stick that in the fstab file, as 
/dev/sda5 /mountpoint  vfat rw,john	0	0
I want to make sure I got it right before I go nosing around in there...

---

### Post by Vishnu V on 2012-02-12
yes append the line to fstab, and make sure /mountpoint exists
comment other entries containing /dev/sda5 use # to comment

---

### Post by jamedfor on 2012-02-12
OK, I edited the fstab file, but upon startup I get a message telling me there was an error mounting /drivemount (the directory I made to mount into)

---

### Post by Vishnu V on 2012-02-12
Sorry,
rw,username doesn't seems to work with vfat. 
change that line to following (where UID is your userid )
```

/dev/sdb5 /drivemount vfat uid=UID 0 0

```

To find uid use following command
```

id -u john

```

you need not restart to remount it, use
```

umount /dev/sda5 #tounmount directory if it is already mounted
mount -a # to mount all file systems mentioned in fstab

```

Tested in ubuntu  12.04

---

### Post by dcstar on 2012-02-13
> **jamedfor said:**
> OK, I edited the fstab file, but upon startup I get a message telling me there was an error mounting /drivemount (the directory I made to mount into)

Post the contents of the /etc/fstab file and also the output of:

```
ls -al /drivemount
```

---

### Post by jamedfor on 2012-02-13
I was about to send another unsuccessful reply when I listed the contents of the drivemount folder.  Everythings there with full access!  It doesnt show up as a seperate drive, but I can get over that.  I'll restart to make sure it mounts on boot, but I think Ive got it from here.

Thanks a lot for the help guys!

---

