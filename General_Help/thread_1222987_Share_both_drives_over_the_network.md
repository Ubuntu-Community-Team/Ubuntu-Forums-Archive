---
title: "Share both drives over the network?"
date: 2009-07-25
forum: General Help
---

### Post by brianzbl on 2009-07-25
Hey everyone. I just installed Ubuntu 9.04 and I'm a bit of a noob. I have SMB up, everything is updated, with the sharring services installed, however I cannot figure out how to make both of my hard drives available over the network so everyone can read/write from them. What is the easiest way to get this done?

---

### Post by swerdna on 2009-07-25
> **brianzbl said:**
> Hey everyone. I just installed Ubuntu 9.04 and I'm a bit of a noob. I have SMB up, everything is updated, with the sharring services installed, however I cannot figure out how to make both of my hard drives available over the network so everyone can read/write from them. What is the easiest way to get this done?

Simply share the mount points (directories). If you tell us the filesystem, I could suggest a configuration.

---

### Post by Prospero2006 on 2009-07-25
> **swerdna said:**
> Simply share the mount points (directories). If you tell us the filesystem, I could suggest a configuration.

Read the configuration file /etc/samba/smb.conf

It defines shared resources.

---

### Post by brianzbl on 2009-07-25
> **swerdna said:**
> Simply share the mount points (directories). If you tell us the filesystem, I could suggest a configuration.

I need to share my home directory which is /home/brian and I also need to share /media/DRV2_VOL1. I read though the smb.conf, but I dont understand where to add sharepoints.

---

### Post by doas777 on 2009-07-25
at the bottom of the smb.conf, you have a series of blocks that define shares. heres one of mine:
```

[manga]
    comment = manga
    path = /media/archive/Media/Manga
    read only = No
    guest ok = Yes
    locking = No

[video]
    comment = video
    path = /media/archive/Media/Video
    read only = No
    guest ok = Yes
    locking = No


```

yours could be:
```

[DVR2]
    comment = DVR2
    path = /media/DRV2_VOL1
    read only = No
    guest ok = Yes
    locking = No

[brian]
    comment = brian
    path = /home/brian
    read only = No
    guest ok = Yes
    locking = No

```

---

### Post by swerdna on 2009-07-25
Regarding DRV2_VOL1:

The approach depends on the filesystem, so let's assume this is an ext3. You said you want it writeable by everyone. If you use a simple guest ok = yes you will have a files and directories belonging to "nobody" -- difficult to administer. It's better if you create a user e.g. sambauser, or billybob, or just use yourself, e.g. brian. Then run this command on the mount point:```
sudo chown billybob:billybob /media/DRV2_VOL1
```. Maybe you also have to chown the files and directories on the partition by including -R option in the command. Then use this form:
```
[DVR2]
    comment = DVR2
    path = /media/DRV2_VOL1
    read only = No
    guest ok = Yes
    force user = billybob
```

The administrative user behind the scenes (sambauser or billybob or whatever) is invisible to the network users who see all files as their own IIRC. You don't need to enrol anyone in the Samba user database, not even billybob.

---

### Post by brianzbl on 2009-07-26
Alright I got it, that was prety easy. Thanks!

---

