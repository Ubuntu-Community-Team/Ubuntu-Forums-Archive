---
title: "Why Killing processes at the startup????"
date: 2010-02-21
forum: General Help
---

### Post by arayici22 on 2010-02-21
Why each boot-level consist of shell-scripts that start and stop processes? Why does the system while booting not just simply add the necessary programs for the next level by starting them, thus making the stopping of specific tasks not necessary and certainly speeding up the boot process? 
:(:(:(:(:(

---

### Post by arayici22 on 2010-02-22
:( No body knowns???????????

---

### Post by mcduck on 2010-02-22
because sometimes you need to move *backwards* in runlevels.. If the extra processes don't get stopped that wouldn't be possible.

For example if you want to move back from runlevel 3 to runlevel 1 you must stop the graphical desktop, otherwise it's not runlevel 1 you end with.

Anyway, all of this will be more or less irrelevant in a while since Ubutnu is moving from the old runlevel-based system to even-based one. Even now most of the traditional runlevels aren't actually used for anyhting in Ubuntu (or Debian).

---

### Post by arayici22 on 2010-02-22
[FONT=Arial][SIZE=2]I can understand that, to move from GUI to CLI we need to kill graphical desktop.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]What I couldn't understand is; We have 6 different run levels and all of them starting and killing processes at the start-up. I can understand to starting programs like if level 3 run graphical desktop. But why Killing? We don't need to even start some programs in some levels but there is script to kill that programs. can we  not just start what we need? what is the purpose of killing programs at the start-up?:confused:[/SIZE][/FONT]

---

### Post by mcduck on 2010-02-22
> **arayici22 said:**
> [FONT=Arial][SIZE=2]I can understand that, to move from GUI to CLI we need to kill graphical desktop.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]What I couldn't understand is; We have 6 different run levels and all of them starting and killing processes at the start-up. I can understand to starting programs like if level 3 run graphical desktop. But why Killing? We don't need to even start some programs in some levels but there is script to kill that programs. can we  not just start what we need? what is the purpose of killing programs at the start-up?:confused:[/SIZE][/FONT]

Well, how can you know from what runlevel the user would move to other? You can't, so you need to kill everything that is not supposed to run on the target runlevel. That's the only way to get only the certain set of services running on that runlevel.

Don't worry about performance, if something is not running then trying to kill it won't cause any noticeable performance hit.

(and no, Ubuntu doesn't really have 6 different runlevels. Runlevels 2&#8211;5 are all the same and most of the system has already actually moved away from the runlevel system)

edit: Here's an example (assuming you'd be runnign a Linux system that uses all the traditional runlevels):

You are currently running on runlevel 5 (multi-user, networking, graphical desktop). You wish to move to runlevel 1 (single user, no networking).
If each runlevel only *started* services, how would you get rid of all the services (multiuser environemtnt, graphical desktop and networking) you need to shut down to get to runlevel 1? And if you don't shut down those services you never actually get back to runlevel 1, instead youd end runnign all the same stuff as in runlevel 5 no matter how hard you try to move to lower runlevels. So the scripts that execute when you move to runlevel 1 must stop networking, multiuser environemtn and graphical desktop even though that seems stupid during the boot process when you are actually moving from runlevel 1 upwards and would only need to add mor and more services.

In the same example, if you instead moved from runlevel 3 (multiuser, network, no GUI) to runlevel 1 you'd need to stop multiuser and network services instead of multiuser, network and GUI as in the first example. Of course you could on each runlevel run a check to see what services are running to find out which ones you need to kill, but that would require a _lot_ more work than simply trying to kill everything that's not supposed to run on the target runlevel.

---

### Post by arayici22 on 2010-02-22
Thanks mcduck i think i understand:D

---

