---
title: "Flash IDE drives are great"
date: 2010-11-16
forum: General Help
---

### Post by Cool Javelin on 2010-11-16
Is there any automated software/drivers/setups out there that will allow me to use one smaller hard drive as a buffer for another much larger hard drive?

I have my ubuntu server 10.04 booting from 2ea. 1GB IDE flash drives. One drive has / (with home and everything except...) the other has /usr.

I have a couple of large (80GB) regular hard drives too that I enjoy spinning down when not needed for noise and power.

This server is intended to be a music server, and a video capture machine.

I am capturing video to a directory on one of the flash drives, and periodically move those 'snapshots' to the large hard drive.

Similarly, I move some music files from the hard drive to the flash drive and feed MPD from the flash drive.

This allows me to spin down the hard drive for long periods of time and use the flash as a "buffer"

Currently, I am using cron to shuttle files back and forth and motion and MPD don't know about the large hard drives.

It is working, but is kind of a PITA as I need to write some smart scripts.

It would be nice if Linux could automate some of that work.

Thanks, Mark.

---

