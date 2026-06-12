---
title: "CPU frequency drops down and stays down"
date: 2011-05-18
forum: General Help
---

### Post by se2131 on 2011-05-18
I'm not sure if this is an issue with Ubuntu or with the BIOS. Basically when I start up my computer, the ondemand governor seems to work just fine (ranging from 800 MHz to 2200 MHz). However after some indeterminate amount of time, it will get stuck at 800 MHz and I'm not able to figure out how to get it to scale properly again. 

When I restart my computer, it acts normal again for some time before locking in at the lowest frequency.

It seems like it may be related to this post: [http://ubuntuforums.org/showthread.php?t=1628479](http://ubuntuforums.org/showthread.php?t=1628479) . The last post in that thread mentioned that it could be related to the temperature, that may be the case in my situation. Even if the temperature is low after it locks to the lowest frequency, it won't increase the speed as needed

My question is, is there any way to override this and let the CPU continue to run at higher frequencies once it locks down to the lowest frequency? My computer doesn't feel like it's getting that hot (it's a laptop), and I'd like to not have to be able to restart it every time this happens.

---

### Post by se2131 on 2011-05-19
Anybody have any suggestions on what I can do? This is basically making my computer useless for a lot of tasks

---

### Post by wildmanne39 on 2011-05-19
> **se2131 said:**
> Anybody have any suggestions on what I can do? This is basically making my computer useless for a lot of tasks

Hi, it will only go up when your system is running programs that need more cpu, that way it saves energy and does not heat up your system when it is not needed.

---

### Post by wildmanne39 on 2011-05-19
> **se2131 said:**
> I'm not sure if this is an issue with Ubuntu or with the BIOS. Basically when I start up my computer, the ondemand governor seems to work just fine (ranging from 800 MHz to 2200 MHz). However after some indeterminate amount of time, it will get stuck at 800 MHz and I'm not able to figure out how to get it to scale properly again. 
Hi, you can change the setting to run the performance setting all the time, but sense you are running a laptop and it really is not needed I do not recommend it, maybe something else is going on that makes you think there is a problem, like how much memory do you have.

When I restart my computer, it acts normal again for some time before locking in at the lowest frequency.

It seems like it may be related to this post: [http://ubuntuforums.org/showthread.php?t=1628479](http://ubuntuforums.org/showthread.php?t=1628479) . The last post in that thread mentioned that it could be related to the temperature, that may be the case in my situation. Even if the temperature is low after it locks to the lowest frequency, it won't increase the speed as needed

My question is, is there any way to override this and let the CPU continue to run at higher frequencies once it locks down to the lowest frequency? My computer doesn't feel like it's getting that hot (it's a laptop), and I'd like to not have to be able to restart it every time this happens.
Aslo how do you know it does not increase the speed when needed. do you have a way of seeing it. It will only increase for a split second at a time if that is all that is needed. Like mine I have 4 cpu's so it almost never increases but when it does it is only for a split second at a time, so if I am not watching my read out I will miss it.

---

### Post by se2131 on 2011-05-19
Thanks for your replies. I have the CPU scaling applet in my panel. Sometimes it shows the frequency going up to 2.2 GHz for both cores when needed (e.g. watching a HD video or something). But at some point during my session, it will stay stuck at 800 MHz for both cores no matter what I'm doing (I'll be running at 100% CPU at that speed), and it stays that way for the rest of the session (and everything runs choppy then).

---

### Post by mc4man on 2011-05-19
If your cpu temps reach the scale down threshold for that cpu then you'll be locked at the min. frequency even when the temps have been reduced below that theshold or even return to normal

---

### Post by wildmanne39 on 2011-05-19
> **se2131 said:**
> Thanks for your replies. I have the CPU scaling applet in my panel. Sometimes it shows the frequency going up to 2.2 GHz for both cores when needed (e.g. watching a HD video or something). But at some point during my session, it will stay stuck at 800 MHz for both cores no matter what I'm doing (I'll be running at 100% CPU at that speed), and it stays that way for the rest of the session (and everything runs choppy then).
HI, my laptop ran hot, I bought one of those laptop pads with the fans to put it on and that helped a lot. Also if you system is more then six months old it is a good idea to clean it out.

---

### Post by se2131 on 2011-06-23
So a bit of an update. If I leave my laptop unplugged when I boot up, and then plug it in when the desktop shows up, then it will stay at 2.2GHz. 

HOWEVER, if I unplug it and plug it back in, then it goes down to 800MHz and stays there no matter what I do. 

Then if I restart the computer in the way I described, it's back to 2.2GHz again

Any ideas on how to prevent this or figure out what's going on? I'm not so sure it's related to the temperature anymore

---

### Post by wildmanne39 on 2011-06-23
> **se2131 said:**
> So a bit of an update. If I leave my laptop unplugged when I boot up, and then plug it in when the desktop shows up, then it will stay at 2.2GHz. 

HOWEVER, if I unplug it and plug it back in, then it goes down to 800MHz and stays there no matter what I do. 

Then if I restart the computer in the way I described, it's back to 2.2GHz again

Any ideas on how to prevent this or figure out what's going on? I'm not so sure it's related to the temperature anymore
Hi, check in power management settings and see you you can change the setting there for when you are on battery, but it sounds like it might be a bug.

---

### Post by se2131 on 2011-06-23
Thanks for the quick reply. When I check in power management, it doesn't say anything for speed. Under the "On Battery Power" tab, the options are "put computer to sleep when inactive for...," "when laptop lid is closed," and "when battery power is critically low". Is there a different application that I need to look at?

---

