---
title: "All i want to do is delete my windows hard drive"
date: 2011-12-27
forum: General Help
---

### Post by nothreat33 on 2011-12-27
First I installed windows 7 ultimate on another hard drive to delete my older installation (of windows 7) on a 500gb hard drive. It wouldn't allow me to. Then i installed kubuntu and open up the partition manager but the option to delete the drive is not available. 

I tried to just delete the files in ubuntu which seemed to work until the trash filled up, when i emptied it completely and tried deleting the rest of the drive I get an error that doesn't allow me to delete the files because my trash is full, even though when i open it there's nothting there. So I took away the option to have a maximum limit and then tried to delete the files again. STILL got an error that the trash is at the maximum limit and to delete it manually.  (the drive i'm using to delete the files on the other drive with  (ubuntu) has enough space to house the deleted contents in the trash until i delete the trash)

i tried rm -R <hard drive> ran the command and it just returned me to the console without any message, error or anything. 

all i want to do is delete the contents of another hard drive on my system.  I've been trying for 2 and a half hours for something that should take a few minutes.
why is this not working.

I'm using 11.10 64 btw

---

### Post by restorator on 2011-12-27
If there is nothing sensitive on the drive just use gparted to remove/delete the partition and create a new one. This would only take a minute and be about the same security level as deleting the files the way you are now or slightly better.

---

### Post by donsy on 2011-12-27
Make sure the partition isn't mounted before you try to delete it.

---

### Post by Mark Phelps on 2011-12-27
Since you're using 11.10, you can use Disk Utility to remove the unwanted partitions.  Find it using Dash.

---

### Post by utnubuuser on 2011-12-27
Easiest to do from a liveCD...

---

### Post by nothreat33 on 2011-12-27
unmounting and then deleting worked. thanks. I assumed it had to be mounted in order to do anything at all with it. ugh.

---

### Post by jwbrase on 2011-12-27
> **nothreat33 said:**
> unmounting and then deleting worked. thanks. I assumed it had to be mounted in order to do anything at all with it. ugh.

It has to be mounted to do pretty much anything *but* repartitioning with it. It has to be unmounted for repartitioning to make sure that nothing but the partitioning program writes to the disk while repartitioning is in progress.

An analogy: Your car has to be running for you to drive anywhere with it, but you have to turn it off to change the spark plugs.

---

