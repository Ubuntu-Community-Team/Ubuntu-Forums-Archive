---
title: "Plymouth fast, but loading GNOME takes AGES!!!"
date: 2010-05-08
forum: General Help
---

### Post by Speed_arg on 2010-05-08
It takes like 8 sec to get into the login screen, but 28 sec to log in the user (its a fresh install, no programs installed)

If it is somehow useful, the ubuntu sound is played immediately.
On this machine

[http://valid.canardpc.com/show_oc.php?id=1175020](http://valid.canardpc.com/show_oc.php?id=1175020)

Unless the "10 secs boot" is just for i7 machines, there is something really wrong :S

---

### Post by jocko on 2010-05-08
> **Speed_arg said:**
> It takes like 15 sec to log in the user (its a fresh install, no programs installed)

On this machine

[http://valid.canardpc.com/show_oc.php?id=1175020](http://valid.canardpc.com/show_oc.php?id=1175020)

Unless the "10 secs boot" is just for i7 machines, there is something really wrong :S
It's not only i7 machines that boot in less than 10 seconds. My core i5 boots in less than 6 seconds.
One thing you didn't say is what type of hard drive you have. I'm pretty sure you will need a SSD drive to get below 10 seconds.

---

### Post by Speed_arg on 2010-05-08
> **jocko said:**
> It's not only i7 machines that boot in less than 10 seconds. My core i5 boots in less than 6 seconds.
One thing you didn't say is what type of hard drive you have. I'm pretty sure you will need a SSD drive to get below 10 seconds.

That's not the issue. In 9.04 from login screen to desktop it was pretty fast, in 10.04 it is SOOOO SLOW. Anyway, i'm not asking for a 10 sec boot, I know with my 7200rpm 500gb drive it won't reach that, but now is slower than 9.04 because from login screen to desktop it takes a lot of time.

---

### Post by warfacegod on 2010-05-08
My guess at the moment would be your ATi card. If you don't have the proper driver running, it could take some time to get everything animated. Especially if you have allot of Compiz effects running, transparencies and the like.

Did you install the 32 or 64 bit version of Lucid?

---

### Post by bumanie on 2010-05-08
I have had this problem since alpha 3. I know one work-around is disabling floppy drive in bios if your computer does not have a floppy drive physically installed. In my case, I have had my floppy drive disabled since 9.10 - so that is not what is causing my problem. Hope this works for you - from login to desktop takes 27 seconds on my computer (so yours is quite quick in comparison). Maybe you should add to the bug report on launchpad if disabling fdd in bios does not help. 
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/534040](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/534040)

---

### Post by Speed_arg on 2010-05-08
> **warfacegod said:**
> My guess at the moment would be your ATi card. If you don't have the proper driver running, it could take some time to get everything animated. Especially if you have allot of Compiz effects running, transparencies and the like.

Did you install the 32 or 64 bit version of Lucid?

I'm using the open-source drivers, they are supposed to be faster (and I feel that) with X.org, aren't they? And I have had no problem with them (unless this is a problem)

Will try the floppy stuff and using ATI drivers to see what happends.

---

### Post by Speed_arg on 2010-05-08
Sorry for double posting. I have re-cheked.

Time to GDM: 8 secs
Time from GDM to desktop: 28 secs

And, if it is useful, ubuntu sound is played immediately.

---

### Post by Speed_arg on 2010-05-08
Wow sorry for triple posting. Disabling A: unit fixed it! Now it is fast :P Can anybody fill this bug? I'm lazy for creating a launchpad acc.

PD: How can I tag it as solved? Editing main thread doesn't allow me.

PD2: Now 14 secs to desktop ;)

---

### Post by warfacegod on 2010-05-08
Scroll to the top of the Thread. Its under Thread Tools.

---

