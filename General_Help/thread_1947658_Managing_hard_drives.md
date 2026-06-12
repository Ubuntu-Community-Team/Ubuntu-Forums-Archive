---
title: "Managing hard drives"
date: 2012-03-27
forum: General Help
---

### Post by cossiemodo2000 on 2012-03-27
Hello everyone, I am new to the Ubuntu world, but I am getting addicted very fast! 

I have two hard drives on my computer, both are 60gb in size, ubuntu 11.10 is installed on one, I have mounted the other post installation of ubuntu. I use the second drive to store pics, movies, and music, i was wondering if i could use it to take off the load from the other disk, in other words if i could run programs from it, or to combine both drives as one. Any help is greatly appreciated.

                                                                                                                                     Thank you

---

### Post by FreeD01 on 2012-03-27
To combine those disks and use it as one volume you probably want to check:

[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

It covers volume groups and logical volumes which is what you are looking for.

You should be able to run apps from it already.

---

### Post by CharlesA on 2012-03-27
> **cossiemodo2000 said:**
> Hello everyone, I am new to the Ubuntu world, but I am getting addicted very fast! 

I have two hard drives on my computer, both are 60gb in size, ubuntu 11.10 is installed on one, I have mounted the other post installation of ubuntu. I use the second drive to store pics, movies, and music, i was wondering if i could use it to take off the load from the other disk, in other words if i could run programs from it, or to combine both drives as one. Any help is greatly appreciated.

You can set the second drive as your home directory, but if you stick to the repos for your programs, which you should, they will be installed on the main drive.

The other thing you can do is combine the drives using LVM, but that would just make both drives appear as one, but I wouldn't recommend it.
See here: 
[http://serverfault.com/questions/222000/lvm-vs-raid0-vs-raid-linear-combine-2-disks-as-one-data-recovery](http://serverfault.com/questions/222000/lvm-vs-raid0-vs-raid-linear-combine-2-disks-as-one-data-recovery)

---

