---
title: "Help me undo the damage of Storage Device Manager (PySDM)"
date: 2009-09-19
forum: General Help
---

### Post by triplesick on 2009-09-19
So I wanted to automatically mount a partition at boot, and read that the easiest way for newbs to do this was with pysdm.  I downloaded pysdm through synaptic.  I succeeded in getting my partition to mount at boot, but pysdm caused more problems than it solved.  now my shortcuts to folders on that partition are broken, and if i unmount the partition and try to remount it, i am now told i do not have permission to do so.  lol wut?

1. will uninstalling pysdm revert the changes it made?

2. if not, is there any way to revert the changes?

3. if not, is there any way to revert to out-of-the-box ubuntu partition-mounting boot defaults?  that is, mount no partitions, and allow me to mount them myself, without being told i don't have permission?

---

### Post by The Cog on 2009-09-19
> 1. will uninstalling pysdm revert the changes it made?
No, I'm afraid not.
> 2. if not, is there any way to revert the changes?
Have a look in /etc and see of it left a backup copy of fstab. I don't know if it does or not.
> 3. if not, is there any way to revert to out-of-the-box ubuntu partition-mounting boot defaults?  that is, mount no partitions, and allow me to mount them myself, without being told i don't have permission?
To work outside your home directory, you need to assume extra privilidges. You can get a command prompt as root (the administrator) by using this command at the prompt:
**sudo -i**
and you can launch a file manager with full root priviledges using this command:
**gksu nautilus**

If you are really stuck, post the contents of your existing /etc/fstab here, and we'll have a look at it. Also, tell us which drives you like to mount manually.

---

### Post by triplesick on 2009-09-19
yes yes sir or madam, there is certainly an fstab.bak file in the etc folder!!  i will use this to replace the other fstab file in the etc folder...if you do not hear from me, take it to mean that this solution failed miserably, and that my computer has become a useless desk decoration.

---

### Post by triplesick on 2009-09-19
restored the file, no change.  after further investigation into pysdm, it seems like it should be possible to modify settings via pysdm so that i will once again have permission to mount.  okay, i changed the settings and still am not able to mount, but perhaps i need to restart.

this is so dumb, before i messed it up, it just asked for a password.  moral of the story: let sleeping dogs lie, curiosity killed the cat, if it ain't broke don't fix it, etc.

EDIT: okay, restarted, and the problem is pretty much solved.  i got the link to "my documents" working by just making a new one, i set up pysdm to mount the partition at startup, and I clicked the box that should have given me permission to mount/umount.  there would seem to be a weird bug, though; i have permission to unmount the drive, but not to mount it again.  which is dumb.  but it's cool.  everything works.

---

