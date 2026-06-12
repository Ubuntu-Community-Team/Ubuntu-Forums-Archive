---
title: "Help finding files on crashed system"
date: 2010-11-30
forum: General Help
---

### Post by sptrsn on 2010-11-30
I had install 8.10 on a machine and was using it as a file server. 
A few months ago I installed 10.04 at a mount point within the main hard drive to try it out. (At least that's what I think I did)

I attempted to upgrade 8.1.....Not sure what happened, but the machine will not boot to the 8.1 install, and now only boots to the 10.04 install. 

Can anyone tell where (if at all possible) to find all the old folders and files that were shared in the 8.10 file structure??

Thanks in advance.

---

### Post by galvatron408 on 2010-11-30
I'm still new to ubuntu so perhaps there is a ubuntu way of doing this but if it was just me..... I would....

sudo fdisk /dev/sda

and then, press "p" to print the partition table. After that, you should see what is supposed to be there. Just mount what you think you saw.

---

### Post by sptrsn on 2010-12-01
Ok. That helps me remember that yes, /dev/sda1 is where that original install is located. It does not however give me any clue as to how or where to find the files associated with that install.

Where would I go from here?

---

### Post by NCLI on 2010-12-01
First, please post the output of these two commands, so that we know exactly how your partitions are laid out and used:
```
fdisk -l
cat /etc/fstab
```

---

### Post by sptrsn on 2010-12-03
As it turns out, that second install was on a separate hard drive and in fact my primary drive has failed.
Thanks for the help.

---

