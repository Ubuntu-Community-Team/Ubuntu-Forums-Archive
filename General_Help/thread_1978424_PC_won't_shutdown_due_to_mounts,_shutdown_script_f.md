---
title: "PC won't shutdown due to mounts, shutdown script fails?"
date: 2012-05-11
forum: General Help
---

### Post by jonathansfl on 2012-05-11
Greetings
Using Ubuntu 12.04LTS desktop (gnome).
My app requires network shares to be mounted in the fstab.
When i manually disconnect the mounts, then shutdown, i have no problem.
However when I try to shutdown without manually unmounting first, Ubuntu freezes forever.
 
I tried to create a shutdown script to manually unmount my shares, but it seems to have no curing effect.
 
sudo nano /srv/K1unmount_on_shutdown.sh
 
(in that file)
```
 
sudo umount /srv/images
sudo umount /srv/logos

```
 
Then I ran:
```

sudo chmod +x /srv/K1umount_on_shutdown.sh
sudo cp /srv/K1umount_on_shutdown.sh /etc/init.d
sudo ln -s /etc/init.d/K1umount_on_shutdown.sh /etc/rc0.d/K1umount_on_shutdown.sh
sudo ln -s /etc/init.d/K1umount_on_shutdown.sh /etc/rc6.d/K1umount_on_shutdown.sh

```
 
I thought the S31umountnfs.sh would have unmounted my network shares anyways!
 
what am i doing wrong?

---

