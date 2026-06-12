---
title: "Problems with New Installation"
date: 2009-09-26
forum: General Help
---

### Post by am6465 on 2009-09-26
I just installed ubuntu along side XP. I didn't partition the hard drive because ubuntu had the option not to so i figured I wouldn't.  I installed the os and everything is working correctly but when i tried to install updates it told me that my disc is full, but my disc isn't full. Any ideas? Thanks

---

### Post by credobyte on 2009-09-26
```
df -h

```

Let us know the output :)

---

### Post by rreese6 on 2009-09-26
Most likely you installed with the default partition size.
start you box in recovery mode, drop to root prompt.
```
sudo gparted
```
if not found install it.
```
sudo apt-get install gparted
```
once in gparted, you will need to resize the larger partition to make room to expand the Linux partition.
**** IMPORTANT ****
If your other OS is Windows, I suggest that you run defrag in Windows before using gparted
*******************

once you have resized your partition. you will have the room for the updates. I believe the default partition size is 2.5 gig way too small. if you have the room, make the partition 100 gigs that should last you a while..
Let us know how it works out.

---

### Post by bodhi.zazen on 2009-09-26
> **am6465 said:**
> I just installed ubuntu along side XP. I didn't partition the hard drive because ubuntu had the option not to so i figured I wouldn't.  I installed the os and everything is working correctly but when i tried to install updates it told me that my disc is full, but my disc isn't full. Any ideas? Thanks

Sounds as if s/he installed with wubi. 

Did you download a large file in Ubuntu ?

---

### Post by am6465 on 2009-09-26
When i run df -h i get this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   43M  99% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G   92K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  172K  1.8G   1% /dev
tmpfs                 1.8G  520K  1.8G   1% /dev/shm
lrm                   1.8G  2.4M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   12K 1012K   2% /tmp

This makes me feel like [rreese6]("http://ubuntuforums.org/member.php?u=546760") is right about the partition thing. When i trried what [rreese6]("http://ubuntuforums.org/member.php?u=546760") suggested it completely failed. It just said that it wouldn't download. I think it may not have connected to a network but I had an ethernet cable connected and I'm surrounded bu wifi. 

I didn't use wubi, unless ubuntu comes with that also.



EDIT:
I ran gparted in regular boot on the terminal and that worked. I shrank my windows partition but I am unable to increase the linux partition.

---

### Post by Bigneil on 2009-09-26
if i was you, i would run ubuntu from the cd and use the partition tool too completely delete ubuntu from the hard drive, then start with a fresh install and remember to choose your partition size when prompted, there is a graphical interface that pops up and asks where you would like to install and what size of partition. 

and as mentioned earlier i would defrag windows first


this is not the most efficient method, but it's what i would do.

---

### Post by bodhi.zazen on 2009-09-27
> **am6465 said:**
> When i run df -h i get this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   43M  99% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G   92K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  172K  1.8G   1% /dev
tmpfs                 1.8G  520K  1.8G   1% /dev/shm
lrm                   1.8G  2.4M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   12K 1012K   2% /tmp

This makes me feel like [rreese6]("http://ubuntuforums.org/member.php?u=546760") is right about the partition thing. When i trried what [rreese6]("http://ubuntuforums.org/member.php?u=546760") suggested it completely failed. It just said that it wouldn't download. I think it may not have connected to a network but I had an ethernet cable connected and I'm surrounded bu wifi. 

I didn't use wubi, unless ubuntu comes with that also.



EDIT:
I ran gparted in regular boot on the terminal and that worked. I shrank my windows partition but I am unable to increase the linux partition.

It certainly appears you resized (re partitioned) your hard drive.

You need to run gparted from a live CD to resize your linux partition. Then you first need to resize the logical partition -> apply changes then resize your root partition.

---

