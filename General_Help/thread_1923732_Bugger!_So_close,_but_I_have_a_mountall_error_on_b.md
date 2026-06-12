---
title: "Bugger! So close, but I have a mountall error on boot"
date: 2012-02-11
forum: General Help
---

### Post by i3design on 2012-02-11
Hi,

My storage drives werent being mounted on startup. I installed storage device manager (pysdm) and followed guides online to set them to automount.

The error I get is:
[B]mount: unknown filesystem type 'LVM2_member'
mountall: mount /media/sde5 [1066] terminated with status 32
mountall: Filesystem could not be mounted: /media/sde5
Press s to skip or M for manual recovery.[/B]

I have 5 drives. 4 are my storage, one is my OS. The 4 drives I set to automount do automount successfully now on startup but only if I skip the error on startup. The error is (i believe) for my OS drive, which I didnt change any settings for, and is still set on default.

In pysdm SDE5 has the following settings:

Allow any user to mount the file system OFF
The file system is mounted at boot time ON
Allow a user to mount and unmount the file system OFF
The owner of the device can mount it OFF
Allow a group to mount this file system group = OFF
Mount file system in read only mode OFF

I really dont want to screw up my instalation since I dont understand what I am doing at this point. Is anyone able to give me some advice?

Thanks,

James

---

