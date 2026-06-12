---
title: "High CPU usage coming out of nowhere"
date: 2011-04-15
forum: General Help
---

### Post by mitk0o0o0 on 2011-04-15
So 2 days ago everything was working fine, was running apps: Xchat, RuneScape, Firefox, Skype, Pidgin and CPU was calm.

Now on Xchat, Firefox, and Pidgin, it's normally 60-70% if i log on to play RuneScape it's 94-99% which REALLY heats my CPU. My computer turned off 1 time (possibly cause of overheating)?

Has anyone else experienced this strange thing?
I also checked System Monitor and nothing is really using that much of the CPU, everything seems normal. Room is quite cold so it couldn't be the enviornment?

10.10 maverick 32bit

AMD Athlon x64

---

### Post by cymbaline42 on 2011-04-15
There might be dust accumulation.  Try cleaning the computer internals.

Check for a damaged fan or heat sink.

If the fan is working fine, make sure there is sufficient room for air flow.

---

### Post by KegHead on 2011-04-15
Hi!

It sounds like it could be your kernel.

sudo apt-get update

sudo aptitude install linux-image -f

Please advise your results.

KegHead

---

### Post by mitk0o0o0 on 2011-04-16
> **cymbaline42 said:**
> There might be dust accumulation.  Try cleaning the computer internals.

Check for a damaged fan or heat sink.

If the fan is working fine, make sure there is sufficient room for air flow.I will check this right away, could be.


> **KegHead said:**
> Hi!

It sounds like it could be your kernel.

sudo apt-get update

sudo aptitude install linux-image -f

Please advise your results.

KegHeadDoesn't seem to recognize the command i think. :s
```
 sudo: aptitude: command not found
```

---

### Post by WorMzy on 2011-04-16
aptitiude was removed from the default package list a while ago, use

```
sudo apt-get update && sudo apt-get install linux-image
```

This doesn't sound like a kernel issue to me though, any PC running at 100% for a prolonged amount of time will generate a lot of heat. If this heat can't escape, your PC may shut itself down to prevent damage to the CPU. Clear out any dust and make sure there's sufficient airflow (vents aren't blocked, fans are working, etc), and you'll probably be fine.

---

### Post by mitk0o0o0 on 2011-04-16
> **WorMzy said:**
> aptitiude was removed from the default package list a while ago, use

```
sudo apt-get update && sudo apt-get install linux-image
```This doesn't sound like a kernel issue to me though, any PC running at 100% for a prolonged amount of time will generate a lot of heat. If this heat can't escape, your PC may shut itself down to prevent damage to the CPU. Clear out any dust and make sure there's sufficient airflow (vents aren't blocked, fans are working, etc), and you'll probably be fine.
Gonna do that in a few hours but to not waste time, i'll try the suggestions on installing/uninstalling stuff.

Now i get this:
```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```

Sorry but i'm a total noob and i don't understand these stuff much.

---

### Post by WorMzy on 2011-04-16
Do you have the Software Centre or Synaptic Package Manager open, or are you running apt-get in another terminal? If so, that's what's causing that error.

If you're not running any of the above, then you should be okay to manually remove the lock file.
```
sudo rm /var/lib/apt/lists/lock
```

The command should run after that.

---

### Post by mitk0o0o0 on 2011-04-16
> **WorMzy said:**
> Do you have the Software Centre or Synaptic Package Manager open, or are you running apt-get in another terminal? If so, that's what's causing that error.

If you're not running any of the above, then you should be okay to manually remove the lock file.
```
sudo rm /var/lib/apt/lists/lock
```The command should run after that.Thanks, command worked.

Listed ouf alot of stuff after that, and ended up with this:
```
Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter
```
I usualy get that when i do sudo apt-get update too.

I hope it worked and that message is just nothing.

---

### Post by WorMzy on 2011-04-16
You're probably getting that message because you have the LiveCD enabled as a software source. To disable it, go to System -> Administration -> Software Sources ([you may need to enable this menu item first]("https://help.ubuntu.com/community/Repositories/Ubuntu#Missing%20repositories%20in%20Ubuntu%2010.10")), and uncheck the box next to the cdrom label. After you've disabled it, you shouldn't see that message again.

---

### Post by mitk0o0o0 on 2011-04-16
> **WorMzy said:**
> You're probably getting that message because you have the LiveCD enabled as a software source. To disable it, go to System -> Administration -> Software Sources ([you may need to enable this menu item first]("https://help.ubuntu.com/community/Repositories/Ubuntu#Missing%20repositories%20in%20Ubuntu%2010.10")), and uncheck the box next to the cdrom label. After you've disabled it, you shouldn't see that message again.That worked, thank you.

And i guess i installed the thing using that command about the image, i guess i need to reboot to see if there are changes?

---

### Post by WorMzy on 2011-04-16
Well, that package I suggested that you install just ensures that you have the most up-to-date kernel available installed from the repos. If nothing got downloaded then you don't need to restart.

---

### Post by mitk0o0o0 on 2011-04-16
I think the problem is solved, thank you very much! :D

In idle it's now 3-7%
With pidgin running, 7-10%

Now RuneScape (Java), Pidgin, Firefox - 40-50% and thats quite the same in windows with runescape.

---

