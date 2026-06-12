---
title: "Move data across hard drives"
date: 2011-09-23
forum: General Help
---

### Post by EienTatsu on 2011-09-23
I have 2 hard drives in my desktop. 1 2tb drive and 1 1tb drive. I have the 2 tb mounted to my home folder but its full. the 1 tb is nearly empty and is mounted as root. How could I change it to where the 1 tb is still root but the 2tb is only the videos folder and music folder from home and the rest of home is on the 1 tb drive.

Thanks.

---

### Post by Lars Noodén on 2011-09-23
Well, I'm having a hard time visualizing your layout but the transfer can be done with [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html) once you figure out where it will go.

---

### Post by drmrgd on 2011-09-23
> **EienTatsu said:**
> I have 2 hard drives in my desktop. 1 2tb drive and 1 1tb drive. I have the 2 tb mounted to my home folder but its full. the 1 tb is nearly empty and is mounted as root. How could I change it to where the 1 tb is still root but the 2tb is only the videos folder and music folder from home and the rest of home is on the 1 tb drive.

Thanks.

I would guess the best way (althougha bit complicated) is to change the mount point for /home to the 1TB drive (probably create a new partition for it alongside your root partition on that drive).  Then move all of the data except Videos and Music from your old home locate to the new home location.  Finally, you could create symbolic links inside the new /home partition on the 1TB for your Videos and Music folders on the 2 TB drive so that you can navigate to them more quickly.

[Here is a good tutorial on how to move your /home partition.]("http://www.psychocats.net/ubuntu/separatehome")

[And here's another.]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by EienTatsu on 2011-09-23
Thanks I'm trying to cp all the data now. Taking quite a while

---

