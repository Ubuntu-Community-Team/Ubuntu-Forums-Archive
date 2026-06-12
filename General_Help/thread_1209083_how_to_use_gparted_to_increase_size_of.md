---
title: "how to use gparted to increase size of / ?"
date: 2009-07-09
forum: General Help
---

### Post by raymondvillain on 2009-07-09
My / partition is full.

How do I give it more room without having to re-install Jaunty 9.04 (32 bit)?

If I open up System>Administration>Parition Editor I can see all the info.

I'm worried I'll ruin the installation.

Is it possible to re-size the / partition ?  Do I need to use the live CD?

---

### Post by milton1 on 2009-07-09
you need a live cd. gparted cannot modify a partition while it is mounted.

---

### Post by milton1 on 2009-07-09
it should be safe to resize with the live cd, but any partitiom change risks data loss. backup anything you absolutely can't lose.

---

### Post by drs305 on 2009-07-09
Yes, you can resize your /.

Considerations:
Backup all your important data before doing any repartitioning work.
It will need to be run from the LiveCD, SystemRescueCD, gparted CD or equivalent since the / partition cannot be mounted when you perform this operation.
It may take a long time to accomplish the expansion, depending on several factors.

If you need advice as to how to do the repartitioning, the most helpful would be a snapshot of your current gparted screen. Let us know where you want to take the additional space from.

---

### Post by raymondvillain on 2009-07-09
Thanks for all the help.

Here is the output of sudo df -h:

> ~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              18G   18G     0 100% /
tmpfs                 1.1G     0  1.1G   0% /lib/init/rw
varrun                1.1G  340K  1.1G   1% /var/run
varlock               1.1G     0  1.1G   0% /var/lock
udev                  1.1G  188K  1.1G   1% /dev
tmpfs                 1.1G   76K  1.1G   1% /dev/shm
lrm                   1.1G  2.2M  1.1G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb5             1.6G   60M  1.4G   5% /boot
/dev/sdb6              18G   15G  2.4G  87% /home
/dev/sdb12             24G  248M   23G   2% /opt
/dev/sdb11             23G  172M   22G   1% /srv
/dev/sdb8              23G  172M   22G   1% /tmp
/dev/sdb9              79G   17G   58G  23% /usr
/dev/sdb13             27G  197M   26G   1% /usr/local
/dev/sdb10             11G  872M  9.4G   9% /var


I don't know how to add a snapshot of the window in which runs gparted, but the info above is about the same thing.

The / partition is 100% full.

I could use lots of Gigs from /usr/local (/dev/sdb13), or /opt, or /srv, or /tmp.

I'm used to running rescuecd and also the Ubuntu live CD.

Briefly, what are the steps to resizing the / partition?

---

### Post by sdlynx on 2009-07-09
It is actually quite straightforward.  Once you've backed up what you need, boot from ubuntu live disc.  Run System > Admin > Partition Editor.  What you'll want to do is shrink the partitions that you want to, then move them all to one side so that all the unallocated space is together, and then grow the / partition.

---

### Post by raymondvillain on 2009-07-09
Thanks sdlynx.

I will have to try that tomorrow.  Will post any more questions then.

---

### Post by t4thfavor on 2009-07-09
I get email helping offering to help increase the size of my / all the time (couldn't resist)

If you just need more space you could mount another hard disk and move user home directories to it. therefore freeing up all the space previously occupied by all your stuff (It helped me save a bunch of time, and the stress of resizing a partition).

---

### Post by drs305 on 2009-07-09
I see you have a / partition of 18G, plus a separate /home partition.
Unless you have data on your / partition or you know of a reason it consumes so much space, you might take a look at the guide linked in my signature line on recovering lost free space.

Often users forget to empty their trash bins (their's and roots), have very large log files in the /var folder (although I see you have a separate /var as well), or have mistakenly made a backup to the /media folder instead of to an external or other internal partition that was *supposed* to be mounted on /media (especially sbackup operations).

Anyway, you may not need to grow / if there are files on / which you don't know and/or want there.

---

### Post by optikal1 on 2009-07-10
I just installed Ubuntu, but it is installed in a very small partition now, 2.5GB. Looking at GPart, I see there is one partition of 110GB to the left of this, and another 9GB to the right of it. I want to combine the 9GB and this small 2.5GB one. How do I do this? GPart does not show any space when I click on move/resize of the small partition. 

thanks for the help...

---

### Post by drs305 on 2009-07-10
> **optikal1 said:**
> I just installed Ubuntu, but it is installed in a very small partition now, 2.5GB. Looking at GPart, I see there is one partition of 110GB to the left of this, and another 9GB to the right of it. I want to combine the 9GB and this small 2.5GB one. How do I do this? GPart does not show any space when I click on move/resize of the small partition. 

thanks for the help...

optikall,

Welcome to ubuntu. A screenshot of your gparted screen would help, but generally:
Do the things in post #4.
Both partitions must be unmounted and you should be running the LiveCD or another type of 'rescue CD'. In gparted, select the 2.5GB partition by clicking on the graphic, then select "Partition". The "Unmount" option should be 'greyed out', meaning it is unmounted. If "Unmount" is available, select it to unmount the partition. Also do this for the 9GB partition.

Both partitions must be primary partitions or logical partitions. That means both partitions must be either *outside* or both *inside* the extended partition - this is the partition highlighted with a light blue border. So both have to be inside or both outside the light blue box.

You must resize or delete the 9GB partition first. Make sure you don't want to save any data from this partition. All data will be destroyed. Highlight this 9GB partition to the right of your ubuntu partition and select "Delete" and "Apply". Once this is done, the space should be dark gray (empty).

You should now be able to select your 2.5GB Ubuntu partition and select "Move/Resize" and expand it to the right.

---

### Post by optikal1 on 2009-07-13
Thanks a lot for the input. I did what you suggested (with minor variations), and it seems to be working! 
 
So now I have a (almost) 12GB partition with UBuntu installed on it. However, I see the linux-swap space only at about 200MB. Is that a problem or is it okay? Should I increase that space?

---

### Post by drs305 on 2009-07-13
> **optikal1 said:**
> So now I have a (almost) 12GB partition with UBuntu installed on it. However, I see the linux-swap space only at about 200MB. Is that a problem or is it okay? Should I increase that space?

It depends somewhat on how much memory you have and how you use your machine. If you plan to use the hibernate feature you generally need more swap space than if you don't. Most swap partition recommendations are for about 500MB-2GB. You could leave your system the way it is and see if you have any problems. Without knowing your RAM, I would recommend 500MB (up to 1GB maximum). 

If the swap partition is touching and to the right of the ubuntu partition changing the sizes would be simple. If they are touching but the swap is to the left, it is simple but it will take a long time for the resizing so make sure you have a reliable power source before starting.

Another option is to use a swap *file* instead of a dedicated partition. This might be a good option for you. Swap files serve the same purpose but do it in a different manner. I haven't used a swap file but if you search these forums there is information about swap files.

---

