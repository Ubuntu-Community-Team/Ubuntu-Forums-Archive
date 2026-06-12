---
title: "Installing Ubuntu on one partition, deleting it in another"
date: 2011-02-07
forum: General Help
---

### Post by CommuneOfLoon on 2011-02-07
I am running 10.04 on a desktop. I currently have only one partition on my harddisk, with my OS and data all on it. I'd like to create a new partition next to the old one, install 10.04 on it, and delete 10.04 on the old one; thus leaving me with a big partition for data and a little one for the OS, so in case my OS crashes my data is safe.

Is this possible? How would I go about doing this?

Thanks!

---

### Post by mantaboo on 2011-02-07
First create a gparted boot disk using the instructions found here [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). Insert the disk and reboot into the live cd. You can resize a partition and create a new one with the remaining free space, reboot. 
now you can install 10.04 onto the new partition then transfer your files. 

With that said, is there a reason why you need to reinstall 10.04? You could use the newly created partition to store your files without having to reinstall your os then and delete the old one. That just seems like a lot of unnecessary work.

---

### Post by CommuneOfLoon on 2011-02-09
Hmm, so to clarify, I could just use Gpart to make a new partition to store all my data on and then leave the OS on the original partition. If I'm getting this right, then yeah, this makes a lot more sense! Thanks!

How much space would I want to leave for my OS partition?

---

### Post by dino99 on 2011-02-09
what you need to follow:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Krytarik on 2011-02-09
Usually 10 GB for the system incl. home is more than enough, I even have just 8,4 GB, and still 3,2 GB free. Depends on how many users you want to set up, of course.

Additionally I have a 3 GB swap partition.

---

