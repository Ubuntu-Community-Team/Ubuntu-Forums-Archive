---
title: "Ubuntu 11.10 the slowest yet"
date: 2012-02-12
forum: General Help
---

### Post by linuxwalker on 2012-02-12
After installing the latest 11.10 version, I notice that Ubuntu seems slower than it did in the past. I ran ```
top
``` and pushed the ```
'c'
``` key for full command paths, and see that python is now used to run many things, like the update manager, ubuntu one client, and many others (especially right after a boot...after I opened Chrome and came here, there are less python processes running).

Python being an interpreted language is much slower than C. I don't remember python being used to ubiquitously in previous Ubuntu versions.

Does anyone notice that 11.10 is slower than before? Thoughts on the switch to so much python code? I've also had some issues like the software center keeps getting segmentation faults. And something as important as the software center is now run again...by python! It seems backwards in a sense.



----Edit: Adding the following:

On the left, it says I'm using Ubuntu 8.10 Intrepid Ibex, but I'm not. I keep trying to go to the User CP and change it, but it keeps saying that I don't have 50 posts, so I can't change my profile details.

---

### Post by Stu15 on 2012-02-12
i think the latest release runs great, but ii think my boot time has gotten worse, it used to be about 10 seconds, now it feels like 40. although after logging in its still usable as soon as you load, which is better than windows.

---

### Post by Stu15 on 2012-02-12
Im currently doing this, this should help any bootup, i would also suggest uninstalling anything that isnt necessary [http://www.youtube.com/watch?v=_6j05f9SccY](http://www.youtube.com/watch?v=_6j05f9SccY)

---

### Post by Stu15 on 2012-02-12
Tried it, timed my bootup sequence, 35 seconds, thats from pressing enter on ubuntu to a loaded logscreen... pretty bad considering the average is supposed to be about 15 seconds.

---

### Post by dgharmon on 2012-02-12
> **linuxwalker said:**
> After installing the latest 11.10 version, I notice that Ubuntu seems slower than it did in the past

I have noticed, and it seems to be using swap a lot more ....

It also prompted me to update the flash plugin, which I did, after which playing Youtube vids is a bit jittery, didn't used to me. Curiously enough downloading Youtube vids and playing them through VLC shows no such problem ...

---

### Post by hawthornso23 on 2012-02-12
You can cut 10 seconds off your boot time by fixing this error in the bootup sequence.

[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

---

### Post by linuxwalker on 2012-02-12
> **hawthornso23 said:**
> You can cut 10 seconds off your boot time by fixing this error in the bootup sequence.

[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

Thanks for that. Did the procedure and rebooted. Did seem faster on both ends (did not officially measure).

I notice that it took an uncomfortably (from my several-years Ubuntu experience) long time between when I hit "Enter" in GRUB to when the login/password screen appeared. But after I entered the password and hit Enter, it was quick from there.

I think this bug fix quickens the password-to-ready-desktop time. I'm wondering what eats up the time from GRUB to login screen (I mean, I know the kernel loading and all of that, but why so much longer than in previous versions is what I meant.)


By the way, this thread I posted was not just about boot/shutdown time, but time in general. Opening applications, opening the control panel, opening the software center. Everything seems much slower than Linux should be. And I think it's all this Python that's replaced a lot of things. I always prefer the terminal. I just have a shortcut to the terminal on the left-side Unity bar and open everything I need from there as it's quicker and gives more control.

---

### Post by Stu15 on 2012-02-12
i dont see how it would be slow if you have the RAM, i have 3gb and from login to usage its super fast, and i have a undervolt app so my processor is often switching speeds and i dont see much change.

I installed Preloader or something like that the other day, after a bit of usage it gets to learn what you use and preloads them in the cache, which is fine because RAM requires the same power even if empty.

Is there any checks youve done to see how much ram you have free, or how fast your disc is reading / writing?

(Im going to have a look at that boot fix)

---

### Post by Stu15 on 2012-02-12
> **hawthornso23 said:**
> You can cut 10 seconds off your boot time by fixing this error in the bootup sequence.

[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

From reading that, initially it seems as though the fix is for shutdown speed, mine is like 7 - 14 seconds shut down, which is fine/normal i think... but people are reporting that bootup sequence is quicker... so i guess it wont hurt to try.

---

### Post by wolfen69 on 2012-02-12
> **hawthornso23 said:**
> You can cut 10 seconds off your boot time by fixing this error in the bootup sequence.

[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

Thanks for this.

---

### Post by linuxwalker on 2012-02-12
> **Stu15 said:**
> From reading that, initially it seems as though the fix is for shutdown speed...

You're correct about that (and reboot speed as well...at least the shutting down part). My bad for misinterpreting it. It seemed like login-to-ready-desktop time was quicker, but maybe it was always quick. The slow boot time seems to be from GRUB-to-login. And when I say slow, it's relative to earlier Ubuntu versions and other distros. But this could be in my head too...I'll need to time it if I want to be sure (really not feeling like it).


> **Stu15 said:**
> i dont see how it would be slow if you have the RAM, i have 3gb...

I have 4GB RAM and the slow part is again, relative. This is about the normal functioning of Ubuntu once already booted up. I'm used to Ubuntu and previous versions being quick, snappy. It's a user experience thing that I notice a lot. When I develop software I strive to make it snappy as possible without prematurely optimizing. Just preferring efficiency over code simplicity when it makes a big (on the order of tenths of a second or second) difference.

And I think this is again because of so much Python going on and running everything, that was not the case in the past. I've heard a lot more hard drive thrashing as well, which others have also noticed. I'm used to Windows being the one that has that problem, and not Linux. So when I see 11.10 becoming slower and more cumbersome, part of the Linux magic is lost, at least for this particular version.

---

### Post by Stu15 on 2012-02-12
Well, i think im going to downgrade to 10.x so... maybe you should as well? It was much faster. and hopefully wont be a waste of time.

---

### Post by Ubuntist on 2012-03-20
> **Stu15 said:**
> Im currently doing this, this should help any bootup, i would also suggest uninstalling anything that isnt necessary [http://www.youtube.com/watch?v=_6j05f9SccY](http://www.youtube.com/watch?v=_6j05f9SccY)

I've done a lot of what's suggested in the video, but I have a couple of questions.  When I try to remove [FONT=Arial]gwibber[/FONT], I get a message saying that, among other things, [FONT=Arial]ubuntu-desktop[/FONT] will be removed.  That sounds scary.  Is it really OK to remove [FONT=Arial]ubuntu-desktop[/FONT]?

Since I have a dual-core machine, I was going to edit [FONT=Arial]/etc/init.d/rc[/FONT] to ch[FONT=Verdana]ange[/FONT] [FONT=Arial]CONCURRENCY=none[/FONT][FONT=Verdana] to [/FONT][FONT=Arial]CONCURRENCY=shell[/FONT][FONT=Verdana].  Actually, though, what I find is [/FONT][FONT=Arial]CONCURRENCY=makefile[FONT=Verdana].  Should I still change[/FONT][/FONT][FONT=Arial] CONCURRENCY[FONT=Verdana], or should I leave it alone?
[/FONT][/FONT]

---

### Post by Mark Phelps on 2012-03-20
> **Ubuntist said:**
> ...That sounds scary.  Is it really OK to remove ubuntu-desktop?

As you have presumed, NOT, it is not OK to do that.

Ubuntu is not going to be lightening fast simply by removing stuff.  Older versions used less sophisticated desktop graphics, so they drew the desktop items faster.

You could jump to Lubuntu -- but you'd be stepping down to a "lower" version.  Speed comes at the price of flexibility and features.

Hate to say it, but you're really grasping at straws here.

---

