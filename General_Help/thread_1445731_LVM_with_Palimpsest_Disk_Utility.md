---
title: "LVM with Palimpsest Disk Utility"
date: 2010-04-03
forum: General Help
---

### Post by samjbobb on 2010-04-03
Hey all, 

I'm working on setting up a new NAS. I installed Karmic desktop on a 160 GB HD using the default settings. 

Now I've added three 1TB drives and want to make them a RAID-5 array with LVM on that, and 1 ext4 partition. I want to use LVM so I can add drives and expand the array later.

So far I've been using Disk Utility (Palimpsest Disk Utility) and it's been great! A wonderful addition to Karmic! I got the RAID-5 array setup with no problems using disk utility. So now I have a 2000 GB raid-5 array setup in Disk Utility and I need to get LVM setup. 

Problem is: I don't see any sign of LVM in Disk Utility. I've been googling all night and I can't find any documentation for setting up LVM in Disk Utility, just people saying that it's supported. 

I tried installing the lvm2 package, rebooting, and then looking around again. No luck.

So, what am I missing? Should there be LVM options in Disk Utility? Where is it? Is there a better/easier way to configure lvm?

Thanks for your help.

---

### Post by samjbobb on 2010-04-04
bump

Any ideas? 

Has anyone setup LVM with Disk Utility? How did you do it? 

Any help is appreciated!

---

### Post by funtimeswithlvm on 2010-05-20
I am wondering the same exact thing. It seems you can setup raid and many types of partitions, and you can edit the partition attributes to type lvm, but I do not see an option for creating an actual lvm/lvm2 partition. My goal is to create an lvm2 volume on top of an encrypted partition.

Please advise!

---

### Post by samjbobb on 2010-05-31
I never figured it out with Palimpsest. I got my RAID 5 plus LVM setup with the command line utilities based on the tutorials I found from googling. Ignored Disk Utility. Seems like it's a good start, just not there yet.

---

### Post by IanW on 2010-06-04
If you want a GUI app to configure LVM arrays, system-config-lvm is in the repos.

WARNING: There is NO "Are you sure?" window with this app, it will make any changes IMMEDIATELY!

---

### Post by srs5694 on 2010-06-04
> **IanW said:**
> If you want a GUI app to configure LVM arrays, system-config-lvm is in the repos.

There's also kvpm. My experience with both tools is limited, so I can't recommend one over the other.

---

