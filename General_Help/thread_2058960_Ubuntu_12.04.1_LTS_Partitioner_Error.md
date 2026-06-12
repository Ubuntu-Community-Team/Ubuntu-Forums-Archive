---
title: "Ubuntu 12.04.1 LTS Partitioner Error"
date: 2012-09-17
forum: General Help
---

### Post by mreos on 2012-09-17
I booted into newly created Ubuntu 12.04.1 via CD and clicked on the icon Install Ubuntu 12.04.1 LTS to install to 8GB USB thumb drive but ran into the following:

> Some of the partitions you created are too small. Please make the following partitions at least this large:

 / 2.4 GB

If you do not go back to the partitioner and increase the size of these partitions, the installation may fail.

I went ahead anyways to see if it would complete but an error displayed stating it ran out of disk space.

Anyone else run into this and how can I proceed? 8GB USB thumb drive not enough?

---

### Post by carl4926 on 2012-09-17
Never tried installing to a pen drive

But in any case you will need to manually create partitions, rather than let the installer do it.
This way
[https://docs.google.com/open?id=0B3e0lLG3OdqERVNNS0pGNEpDblk](https://docs.google.com/open?id=0B3e0lLG3OdqERVNNS0pGNEpDblk)

---

### Post by mreos on 2012-09-17
I've never used the manual approach so if anyone can list the size/type for each partition or link me to a guide, I will gladly give it a try.  Thanks!!

---

### Post by f8l_0e on 2012-09-17
I would say a 100 MB boot partition, and then the remaining space your ext4 mounted to root. No swap partition.  I wouldn't do this without at least 8 GB of system memory though.

You could also go with the following method of installing to a usb drive:

[http://askubuntu.com/questions/150082/how-do-i-install-ubuntu-from-usb-pen-drive]("http://askubuntu.com/questions/150082/how-do-i-install-ubuntu-from-usb-pen-drive")

---

### Post by carl4926 on 2012-09-17
> **mreos said:**
> I've never used the manual approach so if anyone can list the size/type for each partition or link me to a guide, I will gladly give it a try.  Thanks!!
If you have a swap on your HDD then no need for one of those, but if not, it's:

swap (I would keep it minimal) 1GB
/ (root) ext4, all the remaining space

---

