---
title: "A couple simple questions..."
date: 2006-04-27
forum: General Help
---

### Post by orphenshadow on 2006-04-27
First off, I currently have an ATI 9600 AIW in my ubuntu rig, I have yet to figure out the tv tuner, but thats not a big deal, i also have a Nvidia 6800.. Im wanting to upgrade the ati to the nvidia, will i need to make any changes to the driver setups in ubuntu before changing the cards?


The other thing, is after running cedega, and playing wow on the 9600 AIW, i am almost ready to convert my main system to ubuntu ditching windows completly...  Quake 4, WOW, and Unreal Tournament are all linux compatable, so i am not hurting for windows.  i have two  250 gig hard drives formatted ntfs with all my data movies music ect on it...  if i install ubuntu on my main system is it going to be hard to mount the other two hard drives with read/write access? What all will be involved?

---

### Post by threethirty on 2006-04-27
the only part i can reply to is the ntfs question.  I've do it with things like knoppix but never tried with ubuntu.  I've read sever posts where there have been warnings about ntfs support being in testing, so you may wnat to wait and hear from someone who has experience in this.

---

### Post by echo $USER on 2006-04-27
If you are going to ditch windows completely, why don't you back up everything from your ntfs filesystem to an external source and format and partiton it with ext3.  ntfs can't compete with ext3.

---

### Post by Ramses de Norre on 2006-04-27
Linux isn't able to safely write to ntfs, doing so will most likely break your partition tables which will lead to data loss..
So I'd back up the data and repartition the drives to ext3.

For the video cards: sudo gedit /etc/X11/xorg.conf and set driver to vesa, then shutdown, replace cards, boot and install nvidia drivers (enough guides for that on the forums) and change the driver to the installed nvidia driver (ctrl+alt+backspace to restart X).

---

### Post by orphenshadow on 2006-04-27
Thanks, for the data, the two drives are my main backup... ive been giving some thought into dual booting, I already have an existing windows install, on a raid array, i dont know if i want to risk it dual booting, but if i do dual boot what should be installed first windows/linux? would i be able to just add a ubuntu install to the existing windows install provided i partitioned off a chunk of hard drive space?

---

