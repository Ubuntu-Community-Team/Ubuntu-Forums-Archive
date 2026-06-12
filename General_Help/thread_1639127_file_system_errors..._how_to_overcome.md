---
title: "file system errors... how to overcome ???????"
date: 2010-12-06
forum: General Help
---

### Post by rvchari on 2010-12-06
hey guys,
i ve been using maverick right from the 2nd day it was officially released. a couple of days back i get this errors saying my file system is to be checked. at boot time fsck is invoked but nothing materialises... similarly while shutting down it seems to take ages till the system shuts down. 
i was advised to run live cd. unfortunately i gave my live cd to some one and i dont have any...
do i have to create one ? if so then how do i go abt it ?
i m presently using gnome (desktop as well as netbook) and kde environments....
is there any way i can execute a command to get my file system checked ? and ofcourse fixed up !!! ?

---

### Post by endotherm on 2010-12-06
you can if the disk you want to scan is not mounted at the time. the reason you generally need a live CD to do this is because the \ partition needs checked, and you can't unmount that while the system is running.

---

### Post by philinux on 2010-12-06
> **rvchari said:**
> hey guys,
i ve been using maverick right from the 2nd day it was officially released. a couple of days back i get this errors saying my file system is to be checked. at boot time fsck is invoked but nothing materialises... similarly while shutting down it seems to take ages till the system shuts down. 
i was advised to run live cd. unfortunately i gave my live cd to some one and i dont have any...
do i have to create one ? if so then how do i go abt it ?
i m presently using gnome (desktop as well as netbook) and kde environments....
is there any way i can execute a command to get my file system checked ? and ofcourse fixed up !!! ?

You can run fsck from the recovery mode. Boot up and at the grub menu use the down arrow key to select recovery mode. fsck might just auto run anyway.

---

### Post by rvchari on 2010-12-06
i do choose recovery mode... it just takes lots of time and nothing as such materialises... it keeps telling /dev/sda5 (my / partition) needs to be checked for errors... it ends up without correcting.. finally ubuntu is booted up without hassle. only prob is the long wait to boot it and ofcourse shut down time...
wonder wats wrong !!!

---

### Post by rvchari on 2010-12-06
i have a desktop edition-iso for maverick. can i burn it on a cd and then boot from it ? will that work as a live cd ? atleast to check file systems ?

---

### Post by endotherm on 2010-12-06
> **rvchari said:**
> i have a desktop edition-iso for maverick. can i burn it on a cd and then boot from it ? will that work as a live cd ? atleast to check file systems ?
yeah, that shoudl work.

---

### Post by rvchari on 2010-12-06
thanks endotherm...
will do that and check out...
but its gonna take time, will post later....

---

### Post by oldos2er on 2010-12-06
Run ```
sudo touch /forcefsck
``` to have fsck run at next boot.

---

### Post by philinux on 2010-12-06
> **rvchari said:**
> i do choose recovery mode... it just takes lots of time and nothing as such materialises... it keeps telling /dev/sda5 (my / partition) needs to be checked for errors... it ends up without correcting.. finally ubuntu is booted up without hassle. only prob is the long wait to boot it and ofcourse shut down time...
wonder wats wrong !!!

Ok in recovery mode make sure the partition in not mounted.
Note that is umount and not unmount
```
umount /dev/sda5
```

Then run

```
fsck /dev/sda5 -v
```

If it offers to fix anything hit the Y key.

---

### Post by endotherm on 2010-12-06
> **oldos2er said:**
> Run ```
sudo touch /forcefsck
``` to have fsck run at next boot.
so if there is a file in / called "forcefsck" the system will unmount / and perform a fsck on it?

---

### Post by matt_symes on 2010-12-06
Hi

> so if there is a file in / called "forcefsck" the system will unmount / and perform a fsck on it?Yes, it will force a file system check. 

Actually, i think it runs fsck before mounting the root file system or when its mounted read only. Don't quote me on that though.

Kind regards

---

### Post by rvchari on 2010-12-06
after reboot, fsck did a good check up and threw me options to verify and fix broken packages, etc etc. i did all that and selected normal boot. machine booted fast....

but when i shut down the machine, it took a long time to shut down by showing error messages in some inodes and a real long blah blah...

after a few min of its running such messages, it showed system will halt and halts.

reboot is safe again but shut down gives lots of messages. are there some unnecessary deamons running in background thats not letting the machine shut down fast ?

to brief my usage, at work i boot to my ubuntu and connect to office win machine thru samba. and i connect to net thru proxy.
at home i reconfigure by disabling proxy and connect directly.

does this have any implication ? earlier when i was using lucid, i didnt get such messages and boot and shut down was super fast !!!

---

### Post by endotherm on 2010-12-07
well, anytime you get a message about "some inodes and a real long blah blah..." it;s talking about issues with your filesystem, so somthing is still not right. 
check System -> Administration -> Disk utility 
and check the SMART status of your drive. if it is not healthy, it's time to get a new one. if it is, then the issue is likely with system software.
I'd say it's a serious enough issue to backup and rebuild. if you can't get your disk stable, your PC will never work correctly.

---

### Post by oldos2er on 2010-12-07
> **rvchari said:**
> does this have any implication ? 

Your hard drive could be failing. Next time you boot, run a terminal command **palimpsest** to see what it says (palimpsest is a disk utility).

---

### Post by rvchari on 2010-12-08
hey guys,
problem solved...
i did all of the above tricks and nothing worked...
finally i found out that winbind was the culprit...
me being a novice in unix, i simply used apt-get autoremove and rebooted the system,
its perfect... boot time is around 30 secs for maverick and shutdown time is less than 5 secs !!!!

---

