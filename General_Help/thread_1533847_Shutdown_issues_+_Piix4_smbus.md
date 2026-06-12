---
title: "Shutdown issues + Piix4_smbus"
date: 2010-07-18
forum: General Help
---

### Post by DevWolf on 2010-07-18
So. I happen to own a T20 thinkpad, and thought it'd be a smart idea to get the most out of it by downloading a linux distribution. Long story short, I have Xubuntu on this thing, downloaded from the livecd. 

The battery is the only physical component that I am aware of that has a problem with it on the T20 (the battery is um... dead, to put it bluntly). The HDD has been confirmed to be fine by myself and a third party, and everything else works fine on it (...although youtube videos tend to play with a lot of hiccups with smooth audio).  ANYWAYS. 

Now, every time I try to shut this thing down, it simply WILL NOT shut down. It gets stuck at the Xubuntu screen, and then will stay like that. I have waited up to three hours to see if it was just ungodly slow at shutting down, but I see now that that is not the case. 
It will restart just fine, and can log off fine as well, but pushing it directly to shut down will not work. 
I've installed the latest version of Xubuntu on it. When I had Windows still on the T20, it was able to shut down, so I'm fairly sure it's not a hardware issue.  

I'm rather eh... green when it comes to linux, so I have NO idea what to do to stop this error or fix the shut down problem. D: Anyone know of a way to fix this? Should I be trying for a different linux distribution? I've already tried the original Ubuntu. 


Computer specs: 
IBM Thinkpad T20
Ram: 256 MB
HDD: 30 GB
CPU: Pentium III Intel Speedstep TEchnology
CPU Speed: 700 MHz

---

### Post by Mortesins93 on 2010-07-18
Have you tried running the following command in the terminal:
sudo shutdown -P 0

---

### Post by DevWolf on 2010-07-18
No, I haven't. 
D: I would try it right now, but I just booted up Xubuntu a couple of times, and the task bar at the top is NOT coming up. Trying to reinstall the entire OS now, as I have no idea what else to do. x__X [/size]

---

### Post by DevWolf on 2010-07-18
meh, nevermind. The OS disk wasn't running and I figured the taskbar thing out. X__X Idiot move. 

So. I tried the shut down from the terminal as you suggested, and it just brought the laptop back to the xubuntu screen, where it's been sitting like that for... 20 minutes now. So I'd say that it didn't work.

---

### Post by DevWolf on 2010-07-18
After doing a little more research about the Piix4_smbus error, it doesn't seem to be related to the shutdown issues I'm experiencing.  D: So, now I'm just wondering about the Shutdown problem. 


It's not a HUGE issue, as I can of course just unplug the thing (since the battery is dead, it instantly turns it off), but as that's rather hard on the hardware, I'd hate to keep doing that unless it's the only way.

---

### Post by DevWolf on 2010-07-18
Just keeping this thread alive. Still actively searching for answers!

---

### Post by Mortesins93 on 2010-07-21
Sorry but I don't know what the problem is then, it should shutdown with that command.

---

