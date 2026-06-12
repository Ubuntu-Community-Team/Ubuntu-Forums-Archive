---
title: "Shrinking a partition"
date: 2009-08-20
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-20
i have a problem, i am trying to shrink a partition, so i can DD my external drive to my internal drive. I boot from live cd, using gparted, unmount the partition i want to shrink, when it tries to check the partition, it locks up and will not go past 56%. This is the same when i boot, it wants to autocheck the partition, but it also locks up. 

Is there another program i can use, or a way to shrink the volume without gparted checking for errors? i know there are bad sectors on the drive and think this is why it is locking.

---

### Post by AmerNewbieInDE on 2009-08-20
If i just use the cd and install new to my hard drive, what files must i copy to get all updates including my kernel updates to the new drive..

---

### Post by sedawk on 2009-08-20
If it is a simple "data" partition try alternatives like creating
a tar archive, copying the whole shebang with rsync -av ... or
have a look at partimage.

There might be situations for using "dd", e.g. when copying system
partitions, but on the other hand if you have a backup of /home
(which I always put to its own partition normally, so it is on a "data"
 partition) why not to install the system from scratch anyway.

As long as you haven't installed tons of extra software (make
a backup of "dpkg -l" so see what has been installed) or self-compiled
stuff, reinstalling the operating system is faster and better then
messing around with dd images and the aftermaths...

---

### Post by AmerNewbieInDE on 2009-08-20
problem is, i am running ubuntu off the extrnal, did this to see if i liked it before making place on my internal drive. i have made many updates and changes (inc. kernel 2.6.31RC5) and dont really want to have to do fresh install if possible.

---

### Post by sedawk on 2009-08-20
If you have fast internet connection install from CD and afterwards
run an upgrade:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

There is a package cache on your "old" system at /var/cache/apt/archives
but I'm not sure it is a good idea to copy the packages
from there to your newly installed system to 
try upgrading manually ...

Some computer magazines publish Ubuntu-DVDs that contain more packages
than the Ubuntu-CD/DVD (and might include updates). Check your
local store ...

---

### Post by PRMan on 2009-08-20
You could try using the CloneZilla live CD to make a backup of the bad partition.  Then you could restore it onto a new drive.

---

