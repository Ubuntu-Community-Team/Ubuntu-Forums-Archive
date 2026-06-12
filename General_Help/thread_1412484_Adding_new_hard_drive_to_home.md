---
title: "Adding new hard drive to /home"
date: 2010-02-21
forum: General Help
---

### Post by bamend on 2010-02-21
I ran out of space on my /home directory and added a drive.  I've got it in my fstab file but how do I get Ubuntu to add the space to my /home?  The line I put in fstab is:

/dev/sda5 /media/mynewdrive ext3    defaults     0        2

---

### Post by Barriehie on 2010-02-21
> **bamend said:**
> I ran out of space on my /home directory and added a drive.  I've got it in my fstab file but how do I get Ubuntu to add the space to my /home?  The line I put in fstab is:

/dev/sda5 /media/mynewdrive ext3    defaults     0        2

I don't think your /home can span multiple filesystems, unless you do it with symlinks!  For instance, I've got my Documents, Pictures, and Music on another drive but they're symlinked to my booted /home dir.  Another option is to back it up, move it over to the new drive and then restore what you backed up.  There is a tutorial [here](http://psychocats.net/ubuntu/separatehome) on moving your home partition.

HTH

---

### Post by Barriehie on 2010-02-21
I can't remember what the defaults are but:
```

rw,auto,user,exec
```
works well for me when mounting an additional drive and using a mount point in my $HOME dir.

---

