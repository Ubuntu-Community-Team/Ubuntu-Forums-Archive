---
title: "hard drive spin down - /etc/hdparm.conf"
date: 2010-07-11
forum: General Help
---

### Post by Zenze on 2010-07-11
I am running a file server on my home network (nfs and samba). It has 2 drives, one for storage that is shared and one for the OS. The shares are not accessed all that frequently so I would like to be able to have the storage drive spin down whenever possible to preserve the life of the drive.

I found the /etc/hdparm.conf file. Would this be the best way to accomplish this? I heard it can be dangerous but idk why...

Also a passing thought... Will samba/nfs/something else be randomly accessing the drive all the time? I don't want it to constantly be spinning up and down, that would wear it out even faster.

---

### Post by Zenze on 2010-07-11
Also, is it possible that the drive spins down on its own already? Maybe there is already a setting in the OS or is handled by the drive itself?

---

### Post by kenny_duehit on 2011-04-05
BUMP. I would like to know how to do this as well. Seeing as this is a high google search return, I feel this should be answered.

---

### Post by Dave_L on 2011-04-05
Here's an old example I've used. It causes device /dev/hda to spin down after 20 minutes of inactivity. The values are documented in "man hdparm" (see description of -S option).

```
/dev/hda {
spindown_time = 240
}
```

---

### Post by ThePol1 on 2011-04-06
> **Zenze said:**
> Will Ext4/Samba/something else be randomly accessing the drive all the time? I don't want it to constantly be spinning up and down, that would wear it out even faster.

I'd like to understand if this is the case too. I've also read that ext4 writes journal entries to each drive every 5 seconds which would impact their ability to sleep. Can anyone clarify?

---

### Post by ThePol1 on 2011-04-08
> **ThePol1 said:**
> I'd like to understand if this is the case too. I've also read that ext4 writes journal entries to each drive every 5 seconds which would impact their ability to sleep. Can anyone clarify?

Bump

---

