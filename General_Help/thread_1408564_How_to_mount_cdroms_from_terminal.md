---
title: "How to mount cdroms from terminal?"
date: 2010-02-16
forum: General Help
---

### Post by fleppmar on 2010-02-16
Hi. 

I installed linux 2 days ago. 

Something has gone very wrong!

When I log in, ubuntu 9.10 goes to terminal, nothing else. 
Have tried to reinstall xserver and nautilus, reconfigured both of them. Nothing works. 
I have tried countless times to mount an iso image from various cds and download sites, and now my startup image has changed. 

So my last resort, as I see it is to try to mount the iso from the terminal. 

Have tried this: sudo mount /dev/cdrom
get this answer:  Mount: block device /dev/sr0 is write-protected, mounting read only

get this answer from all the cds. 

Please help! As of now,I have no computer, and really need it at school!
Habe only my phone. 

Regards
fleppmar

---

### Post by nerdy_kid on 2010-02-16
to mount a cdrom:
```

mkdir whereever
sudo mount -t iso9660 /dev/cdrom whereever
cd whereever

```

CDs are always readonly, so your error isnt an error.

for your xserver you could post /var/log/Xorg.0.log and ~/.xsession-errors

---

### Post by cjhabs on 2010-02-16
sudo mount /dev/cdrom /your_mount_point -o ro

---

