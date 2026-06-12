---
title: "OS Hard drive failing"
date: 2011-04-04
forum: General Help
---

### Post by ExTruckie on 2011-04-04
Hello 

I need some advice.  I have an install of Ubuntu acting as a file server with a second hard drive for data storage.
The os drive makes a clicking noise when it is being accessed, usually everything is running in ram. Also I get a lot of disk errors during boot   I will post specs at end.  
I have clonezilla but am unsure how to use it. 
Usually I would buy a new HD and just reinstall but I rather just install an image of the existing install on the new hard drive.

Any advise would be appreciated.

Thanks 

ps I need to learn how to do this anyway so!!! :popcorn:

Specs
AMD Athlon XP 2.9ghz CPU, 2GB ram 30G HD (one Failing) a 320G HD (Data),  DVD Burner, 
Using Ubuntu 10.10 with webmin and RealVNC to administer it.

---

### Post by conradin on 2011-04-04
just clone disk to disk, and save a step in imaging then re-imaging. Boot clonezilla its very straight forward. use beginner mode, select work with disk to disk, use your old hd as the source, and new hd as the target. when it asks if you want to clone the boot loader say yes.

---

### Post by ExTruckie on 2011-04-04
Duh

Also most too easy!!

I just never played round with it and can't afford to mess up.  Just as in the real world. 


I guess Ill try got to get a new drive first, but them are cheep.

Thanks.

---

### Post by conradin on 2011-04-04
then test drive clonezilla with 2 usb drives (unplug your hds) if you need a test run. Duh.

---

### Post by lindsay7 on 2011-04-04
When you clone with clonzilla, it should not change your existing drive.  You can install the new drive and make sure that it is working well before you trash the old drive.

---

### Post by cheapie on 2011-04-05
Can't you just run sudo dd if=/dev/sda of=/dev/sdb or something like that?

---

### Post by Hedgehog1 on 2011-04-05
> **lindsay7 said:**
> When you clone with clonzilla, it should not change your existing drive.  You can install the new drive and make sure that it is working well before you trash the old drive.

+1 on this.  Set the old drive aside after the clone and keep it a while in case you need data off of it again. You can make a door stop of out if later... :)

T***he Hedge***

:KS

---

