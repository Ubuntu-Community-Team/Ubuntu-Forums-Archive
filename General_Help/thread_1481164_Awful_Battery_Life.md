---
title: "Awful Battery Life"
date: 2010-05-12
forum: General Help
---

### Post by adam22 on 2010-05-12
So, I never got great battery life with 9.04 or 9.10, but it was acceptable. 

Here's the thing, with Windows 7 I can get about two hours. With Ubuntu I'm lucky if I get an hour, and I mean really lucky.

I have selected to dim the brightness and to spin down the HDD when possible, it hasn't helped a whole lot. What I don't see is an option to underclock the CPU, which is done rather easily in Kubuntu.

Guidance, please?

---

### Post by blazemore on 2010-05-13
This utility might help!
[http://grano.la/](http://grano.la/)

---

### Post by adam22 on 2010-05-14
I'll check it out...I guess basically I'm looking for a way to go into powersave mode, like Windows and Kubuntu do by default on battery. Will post with results.

---

### Post by HermanAB on 2010-05-14
You have to stop the syslog daemon, else the disk will never spin down.

---

### Post by Nick_Jinn on 2010-05-14
> **HermanAB said:**
> You have to stop the syslog daemon, else the disk will never spin down.



Is that why hard drives die faster?

---

### Post by formaldehyde_spoon on 2010-05-14
What sort of computer s it?
You could try Eeebuntu or Jolicloud; they're both based on Ubuntu and designed for netbooks...
Haven't tried either of them myself yet, so can't say if they are any good.

---

### Post by adam22 on 2010-05-14
It's a full size 15.6" gateway. Runs great, but I need more than an hour on battery. Not sure what you mean by stopping the syslog daemon.

---

### Post by adam22 on 2010-05-14
I installed granola...I seriously doubt it will help, there's not a whole lot you can do with it either. I might be wrong though.

---

### Post by Nick_Jinn on 2010-05-15
Are you using the downclocking CPU function? How much RAM do you have?

You could try disabling your wifi when you are not needing the internet.

Are you using the CPU limiter that Ubuntu comes with?

I guess intel wrote an open source program called powerTop that you can use in linux that will tell you exactly what you can do to save power....whats eating up your battery and what you can do to reduce that.

---

### Post by gear.h34d.2012 on 2010-05-15
Odd. I'm running a Dell XPS M1530 with a T8600 at 2.4GHz, 3 gigs of RAM, and an Nvidia 8600M. I run all effects on, I spin the disks down, and I power use the damn thing on battery fully manipulating all kinds of mess. Average at 3 hours and 15 minutes on battery. O.o

---

### Post by (^_^)Smiley on 2010-05-15
I also had low baterry time with the 64 bit version of lucid. I installed the 32 bit version and now it has much more battery life. I also installed powernowd cpu frequency scaling to save energie it works great!
Sorry for my bad English!

---

### Post by 3rdalbum on 2010-05-15
Even two hours is pretty pitiful battery life.

I'd suggest running Powertop:

```
sudo apt-get install powertop
sudo powertop
```

Use its suggestions.

Also add the CPU Frequency Scaling Monitor applet to your Gnome panel, it allows you to change the scaling governor, and even set what speed you want the CPU to work at. The OnDemand scaling governor is recommended so the CPU can sleep as much as possible, but if you're watching video or doing something that will tax the CPU for a set amount of time regardless of how fast the CPU is running you can drop it to Powersave.

---

### Post by inso_741 on 2010-05-15
try installing laptop-mode ```
sudo apt-get install laptop-mode-tools 
```
also if you have nvidia gfx try using restricted drivers as nouveau has no power management :P

---

### Post by adam22 on 2010-05-15
I'll try powertop...I'm using AMD if that matters though.

---

### Post by adam22 on 2010-05-19
I added the laptop mode and CPU applets and changed them to on demand. Also, powertop made a suggestion that involved USB devices, and now if I don't move the mouse for like 5 seconds, the mouse won't move unless I shake it around for a few seconds...any idea how to reverse this?

---

### Post by kid1000002000 on 2010-05-19
You can also get your display to go even dimmer.  Change the gnome-power-settings by hitting alt-f2 and typing "gconf-editor."  Then find gnomepowersettings in there and decrease the minimum value all the way.  You should find plenty of settings there you can play with, including hard drive spin down times as previously suggested.  If you are using any distro previous to 10.04, kpowersave is also a viable app option.

---

### Post by Zintha on 2010-05-19
2 hours is pretty dismal for any laptop that isn't one of those tiny compact things. Even so i've seen better.

Can't point you to a program but i'm sure google/someone else here has/can/will but you should probally check your battery.

Might be dying, I know my laptop used to hold for hours and hours, now its 3ish at best and I took it in to be checked (other issues too) and they said its natural for batteries to die over years and hold less and less of a charge.

Just a thought!

---

### Post by adam22 on 2010-05-20
It's a year old laptop...It gets 2.5 hours on Windows 7, but only 1 hour on Ubuntu. Clearly, this is not a hardware issue.

I'm going to go back to 9.10 or try Fedora, there's no way I can continue on with this battery life.

It also takes forever to charge the computer in Ubuntu, where as it is much quicker in Windows 7.

---

### Post by ario on 2010-10-30
> **adam22 said:**
> It's a year old laptop...It gets 2.5 hours on Windows 7, but only 1 hour on Ubuntu. Clearly, this is not a hardware issue.

I'm going to go back to 9.10 or try Fedora, there's no way I can continue on with this battery life.

It also takes forever to charge the computer in Ubuntu, where as it is much quicker in Windows 7.

I had a similar problem with acer aspire 5535 laptop with ATI Radeon HD3200 graphic chipset. I noticed that something in linux sets up GPU to 100 performance all the time. I downloaded and installed propriety driver from AMD website (version 10.10) and this reduced power consumption more than 10 watts! Increase battery life time and reduced charge time to what it was on windows 7.
Hope this helps.

---

### Post by joshruehlig on 2010-10-30
You have to make sure tht if you have multiple frequencies you are using them. (Frequency Scaling)

Try the frequency scaling monitor tip, it should show any mode you could use (out of the box, atleast) If you dont see ondemand as on option then you have too find out a way to enable it in your kernel.

If you do have a scaling option choose it and do it for each of your cores/threads.  You can make this perminent too 

```
su
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

And [http://www.lesswatts.org/](http://www.lesswatts.org/)

---

### Post by inso_741 on 2011-04-09
found an easy way to undervolt your processor...you dont even have to compile a custom kernel now everything is already available...here's the [tutorial]("http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/")

---

