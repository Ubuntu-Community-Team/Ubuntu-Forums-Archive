---
title: "Mounting hard drive images"
date: 2009-09-03
forum: General Help
---

### Post by theparticle010 on 2009-09-03
I recently created a set of some hard drive images using the dd command and Got my old windows 98 computer booting up in qemu, however I would like to recover quite a bit of files from the images themselves, now I know that you can mount iso files with a command such as this:

mount -o loop -t iso9660 /home/user/isofile.iso /mnt/isofile

but when I try mounting the image using the command:

mount -o loop -t vfat /home/user/imgfile.img /mnt/imgfile

It just comes out with:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And I have no problems mounting the iso images... The only thing I can think of is that I gave the wrong file system option. I do know that the Image is of fat32 system, and the Image was of the entire device and not just a partition.

---

### Post by P4man on 2009-09-03
You can't mount an entire disk. You can only mount a partition. have a look at this to see how to mount one partition from the entire image:

[http://ubuntuforums.org/showthread.php?p=4432555](http://ubuntuforums.org/showthread.php?p=4432555)

---

### Post by theparticle010 on 2009-09-03
Thanks, thats incredibly useful.

---

