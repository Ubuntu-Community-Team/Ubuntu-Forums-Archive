---
title: "repartitioning tool"
date: 2009-09-07
forum: General Help
---

### Post by robfindlay on 2009-09-07
When I installed UNR  9.04 on my netbook I did my partitions wonky. 

Is there a tool that will let me resize my main linux partition and turn it into a win32 partition?

---

### Post by alejaaandro on 2009-09-07
install gparted.. you'll be able to manage all the partitions EXCEPT  the one where your root is installed (ie, your ubuntu partition. that is because to manage a partition it must be unmounted).. if you want to change that partition you ll have to use a live distro (i love pated-magic (*)) burn it on a disk, boot from it and then you can manage all the partitions in your disk...

since you mention UNR, you might not be able to use a cd, don't worry, i think there is a version for installing on a usb.. if not, on ubuntu install unetbootin and make a bootable usb disk with that.. 

i don't think though that you can convert a partition without formatting it..

(*)edit: it's actually parted magic, not "pated".. here is a [link]("http://partedmagic.com/") thnx drs305

---

### Post by fluffman86 on 2009-09-07
If you want to turn your main partition into NTFS, then the best way to do that is by just installing Windows.  That will completely wipe your hard drive.  I hope that's not what you're wanting :(

---

