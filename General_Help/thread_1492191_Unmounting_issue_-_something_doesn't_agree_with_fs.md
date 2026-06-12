---
title: "Unmounting issue - something doesn't agree with fstab"
date: 2010-05-24
forum: General Help
---

### Post by Gremlyn1 on 2010-05-24
I run an Ubuntu guest in VirtualBox on my XP Pro desktop at work, and recently added a line to my fstab to automount our shared drive (rather than mount each time I need it). It seemed to be working fine for a few days, but I recently restarted the whole system and something has gone wonky. I can still access the drive, no problems there, but I have two instances of it showing up in my Places menu. One is unmounted, and it won't let me mount it or remove it from the list. The other is mounted and I can't unmount it. The error I get is:
```
umount: /media/T_Drive mount disagrees with the fstab
```

My fstab looks like this (blocked out IP Address for security ;)):
```

proc    /proc    proc    defaults    0    0
# / was on /dev/sda1 during installation
UUID=f284eb91-e311-4a50-ae70-e40ea2fc123f    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sda5 during installation
UUID=b7beede9-ad18-4b65-95e1-11add593a291    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660 user,noauto,exec,utf8    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
//[IP ADDRESS]/shared_fs/    /media/T_Drive    smbfs    auto,credentials=/root/.credentials,user    0    0
Shared    /media/shared    vboxsf    defaults    0    0

```

I found some kind of buy back from 2007 that was supposedly fixed, but that's all I managed to come up with... Any ideas? It's more annoying to have two drives sitting there than anything else, at least I can access it still.

---

### Post by Gremlyn1 on 2010-05-25
OK, so I did a ittle messing around, and I can unmount and such as root. What in my fstab is blocking me from mounting/unmounting as non-root?

---

### Post by drknot on 2010-05-25
> **Gremlyn1 said:**
> OK, so I did a ittle messing around, and I can unmount and such as root. What in my fstab is blocking me from mounting/unmounting as non-root?

   Not an expert but similar difficulties using my AA1 and fiddling with fstab  ,
  fstab is run as root at boot 
   add UID=[user] and GID=users as necessary to the line in fstab - this makes the mount belong to the group/user rather than root - hope this helps!

---

### Post by geirha on 2010-05-25
In a terminal, do
```
man mount
```
Then read what the options **users** and **user** does.

---

### Post by Gremlyn1 on 2010-05-25
> **geirha said:**
> In a terminal, do
```
man mount
```
Then read what the options **users** and **user** does.

So you're saying I need to use 'users' instead of 'user'? Having 'user' limits it to the original mounting user, which in my case would be root. Hopefully I read that right in the man page.

EDIT:
I went ahead and set it up with 'users', but still can mount it without root. I'm wondering if the requirement for the /root/.credentials file is screwing me up, since only root can read it. I get following error when trying to mount not as root:
```

error -1 (Unknown error 4294967295) opening credential file /root/.credentials

```

EDIT AGAIN:
After testing if moving the .credentials file helped, I no longer got the above message, but I still getting an error:
```

mount error(1): Operation not permitted
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```
I read through the mount.cifs and mount.smbfs man pages and nothing jumped out as my solution. I also found that I can't edit anything on the mounted drive unless I am root either, which isn't going to be very useful to me :(

---

### Post by geirha on 2010-05-26
The user has read access to the credentials file? what does that fstab line look like now?

---

### Post by dino99 on 2010-05-26
follow the easy way: install mountmanager with synaptic, then tweak it (system admin mountmanager)

---

