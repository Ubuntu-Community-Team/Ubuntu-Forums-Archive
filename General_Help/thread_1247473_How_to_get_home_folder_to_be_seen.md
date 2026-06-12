---
title: "How to get home folder to be seen?"
date: 2009-08-23
forum: General Help
---

### Post by hockey97 on 2009-08-23
Hi, I can't boot into my ubuntu system because I jsut found out on my main system in the home folder it's empty. 

I have 2 hard drives. One is 60gigs and the other is 300gigs. 

the 60 gigs has is all linux and has my root file system. 
I then created a extended partician on the 300gigs hard drive. 

The 300 gig hard drive has a partician for also windows xp.

now my home folder is on my root system on the 60gig hd. So my user folder is on the extended partican on the 300gig hd. When I set this up it worked. I set that up like a year ago. I never had problems. 

Currently I changed permissions on / by mistake and now I can't boot my system because my home folder is missing or has no proper permissions. 

I looked at my home folder on the root and found the home folder empty and  I think somewhere the connect got messed up. I think my system is looking for my user folder at my home folder yet it's on a extended hard drive partician.

So what can I do to make my system understand the user folder is on another partician?

---

### Post by 3rdalbum on 2009-08-23
This involves modifying the /etc/fstab file to mount the new partition at the location "/home".

I take it you know how to open /etc/fstab as root, from a live CD (I assume anyone who's been using Ubuntu since Feb 07 knows).

Add the following line:

```
/dev/sda2 /home           ext3    relatime        0       1
```

Substitute "/dev/sda2" for the device file name of your home partition. If it's not ext3 either, you'll need to change that.

Save changes and reboot, you should be good to go.

---

### Post by hockey97 on 2009-08-23
> **3rdalbum said:**
> This involves modifying the /etc/fstab file to mount the new partition at the location "/home".

I take it you know how to open /etc/fstab as root, from a live CD (I assume anyone who's been using Ubuntu since Feb 07 knows).

Add the following line:

```
/dev/sda2 /home           ext3    relatime        0       1
```

Substitute "/dev/sda2" for the device file name of your home partition. If it's not ext3 either, you'll need to change that.

Save changes and reboot, you should be good to go.

I chcked fstab and it has the right information.

yesterday by mistake I did a chown -R user_name / 

so now I would get a error saying sorry can't find home folder make sure it has the right permissions or make sure the file is at your home folder.
then it asks if I would like to use the root directory as a home folder or something in that area.

I checked the fstab folder using the live cd as root.

do you think it could be permission problems?

what files should I look at to help debug the problem? Like logs

---

