---
title: "Need help restoring default USB-HDD mount settings"
date: 2009-07-13
forum: General Help
---

### Post by coxwebdesign on 2009-07-13
Hi there,

I was playing around trying to sort out a backup system on our server. We have a simple setup of two external toshiba 1TB hard drives, identical models. Only one external drive is ever connected to the server at any one time.

I noticed that when I was restarting the machine, now and again it was assigning the drive different mount points: USB-HDD, USB-HDD_, USB-HDD__, etc.

I right clicked on the drive, went to properties and then clicked on the volume tab - renamed the volume tag to /media/USB-HDD and then copied the other settings from what was already set in the info above, clicked closed, tried to remount the drive and now I am getting the following error message when I try to mount the drive:

libhal.c 1399 : wrong reply from hald. Expecting an Array. org.freedesktop.Hal.Device.Volume.InvalidMountOption

Not really sure where to start with this one :( First thing's first I need to get my drive mounting again, how would I go about doing this since I cannot change the settings associated with the drive since I am no longer able to mount it?

Cheers,

Dave.

P.S. The drive has been working fine up until I messed up the settings (just the problem with the changing mount points that I was trying to fix but screwed up).

---

