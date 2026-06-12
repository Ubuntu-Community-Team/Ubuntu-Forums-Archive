---
title: "mount ext4 partition in hardy heron"
date: 2009-11-26
forum: General Help
---

### Post by karlmp on 2009-11-26
this is what i get in thunar, pcmanfm, and nautilus:

> Cannot mount volume.

The volume uses the ext4 file system which is not supported by your system.



I have a triple boot: xubuntu 8.04, kubuntu 9.10, windows xp

I used to have intrepid where karmic is now and of course it mounted fine because it was ext3

---

### Post by audiomick on 2009-11-26
hallo.
you are trying to mount a partition out of the 9.10 installation into the 8.04 Xubuntu installatio, are you? You don't really say. If that is the case, no, it wont work. You will have to change the partition to ext 3, or update your Xubuntu.

I _**do not know**_ if it is possible to change the file system on a partition without destroying the data in it. You'll have to look that up for yourself

---

### Post by snowpine on 2009-11-26
Personally, I got around this by installing a newer kernel with ext4 support.

All Ubuntu kernels are here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

If you are not comfortable with this, the simplest solution is to boot with an Intrepid or newer Live CD and copy any necessary files to your new Hardy partition. Good luck!

---

