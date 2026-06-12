---
title: "Resizing Partitions..."
date: 2010-12-18
forum: General Help
---

### Post by sKRiBEL on 2010-12-18
I want resize my partitions, i need more space for ubuntu, i already have 58gbs of free space, but i dont know how i can expand my partitions, i have tried "GParted Partition Tool", but it won't allow me to do it. The only other thing i can think of is re-installing ubuntu, and if i have to reinstall it how can i retain my settings and programs that i have installed? any help would be greatly appreciated :]

---

### Post by i_dont_know_what_im_doing on 2010-12-18
I don't think you can resize a partition that is currently in use. You could try booting off your live CD and using GParted from there, or making a GParted live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))

---

### Post by lmarmisa on 2010-12-18
Gparted is the tool you need. Are you sure Gparted does not allow to resize your partitions?. What Ubuntu version are you using?.

Can you post a screenshot of gparted window?.

---

### Post by Girya on 2010-12-18
you need to use gparted from a live cd. you can't resize mounted partitions.
while your at it check out lvm2. its a great way to solve the problem you are having. you can resize volumes (an abstraction of partitions) while the system is up and running. a lot of distros use it as a default partitioning scheme. also check out how to put your /home on its own partion/volume. 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by lbarnes on 2010-12-18
/home partition is definitely the way to go.
Put Ubuntu on 20-40gb partition.

---

### Post by 73ckn797 on 2010-12-18
> **i_dont_know_what_im_doing said:**
> I don't think you can resize a partition that is currently in use. You could try booting off your live CD and using GParted from there...
This is the easiest solution.

---

### Post by sKRiBEL on 2010-12-18
> **i_dont_know_what_im_doing said:**
> I don't think you can resize a partition that is currently in use. You could try booting off your live CD and using GParted from there, or making a GParted live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))
ok i'll give it a try :] thanks

---

