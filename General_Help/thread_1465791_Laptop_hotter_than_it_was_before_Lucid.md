---
title: "Laptop hotter than it was before Lucid"
date: 2010-04-29
forum: General Help
---

### Post by kaldor on 2010-04-29
I upgraded to Lucid today via a fresh install. I've noticed the laptop temperature is much warmer and makes my hand sweat a lot while typing. It feels too hot.

Any reasons why? Are there lots of background processes on Lucid that I am not aware of?

---

### Post by spoon_ on 2010-04-29
Do you have an nvidia card? I read that the new open-source driver included with lucid (nouveau) lacks any power management.

---

### Post by kaldor on 2010-04-29
> **spoon_ said:**
> Do you have an nvidia card? I read that the new open-source driver included with lucid (nouveau) lacks any power management.

I do, yes. But I don't use nouveau due to needing the proprietary one.

---

### Post by kaldor on 2010-04-30
I checked for dust buildup or anything that could be a problem, but it's all clear. It's extremely hot. I can't touch the bottom of the laptop because it's too painful. It's louder too.

Problem with Lucid? My hardware? Maybe the laptop's just old? All I know right now is that it isn't normal for hands to begin sweating after typing a few sentences :(

---

### Post by luisg on 2010-04-30
I can confirm this too, I have an ATI hd 4350, using the default driver installed by Lucid (compiz enabled). Also, battery life seems shorter.

I'll test today with the fglrx driver (which always worked very well on Karmic).

---

### Post by pqwoerituytrueiwoq on 2010-04-30
i read that were was an issue with a driver version from nvidia forget which one
check the performance setting in nvidia's control panel 
i set mine to performance

---

### Post by kaldor on 2010-04-30
I removed proprietary drivers and it is of no change. And yes, battery life is about 20 minutes shorter than it was. 

I'll reinstall the drivers and get back to you about it later. 


This is an issue that really needs to be looked into, it can mess stuff up for people quite badly. As I type this, I have only had my laptop on for about an hour and it is resting on a flat surface (table). It's too hot for me to type easily with and is beginning to slow down.

Edit: Last night while using Skype, I had the laptop in my lap. Ubuntu began to run VERY slowly and got very hot even though the fans were not blocked off in any way. It started to take up to 10 seconds to maximize/minimize windows. I hope Lucid isn't breaking my laptop :(

---

### Post by TBABill on 2010-04-30
Anytime your equipment runs that hot you stand a very high chance of something failing. Even if fans are enabled and working at max speed it will not save your machine from heat damage if the heat level is greater than the fan can remove. I would take the steps to either enable your monitors to find out how hot it is running and whether it is approaching critical levels, or switch distros to something non-Ubuntu based and compare. Don't risk your equipment just to say you use Ubuntu, but there are things you can do to see what the situation really is as far as CPU temp, hard drive temp, etc. Search the forums for advice on enabling easy monitoring for your critical components.

---

### Post by luisg on 2010-05-01
Hi, after installing propietary ati drivers - fglrx, temperature seems to be back to normal, so I guess open source ati drivers still need to mature.

I'll report back if something else arises.

---

### Post by digital-daniel on 2010-05-05
I have the same problem with fglrx drivers and ati card. I'm running around 47°C and up to 80 at times. With Karmic it was low 30°C s. Any suggestions

---

### Post by userdce on 2010-05-14
I too had this problem
It happened only after I upgraded from KARMIC to LUCID and it never recovered
Lastly I had to reinstalled KARMIC

---

### Post by cimh on 2010-05-14
I wonder if this is related to my problem on an eeepc netbook. It runs much warmer than on distros - the cpus rarely drop down to their lower speeds and the fan is running fast.

With karmic and other distros the fans are quiet or off and cpu temp is lower even tho the fans dont run. Running 'sudo powertop' from the terminal shows that a 'kernel scheduler - load balancing tick' is waking up the cpu 498 times a sec. Something that doesnt happen in the other distros where wake ups are usually <200/s so something is driving the thing hard. There are similar reports in other threads. This is enough for me not to use ubuntu until a solution is found as the fans are annoying and the battery is being drained.


cimh
eee901, lucid,lubuntu,puppeee

---

### Post by (^_^)Smiley on 2010-05-14
I also have this problem I thought it would go away, since I upgraded to lucid my fans are running full time and the laptop gets very hot! 
I don´t know what´s going on I think I´ll install karmic again. I hope they will find and fix this problem.
Sorry for my bad English!

---

### Post by cimh on 2010-05-14
Well I have found a partial solution. I have downloaded and boot into the netbook remix launcher and this cools the machine down. Temp is reduced from 62C to 48, fan running slower and wake ups down from 500 to 200. Powertop reports power drop from 12 to 10.5 Watts. So something in the standard lucid package is doing a bad job of power management. 

Sadly I dont like the launcher - IMHO its a slower interface that mimics the android/iphone concept which is great on a touchscreen

cimh

---

### Post by 2hot6ft2 on 2010-05-14
Right click on the top panel and select Add to Panel.
Select CPU Frequency Scaling Monitor.
Click Add then Close.
You can left click on the applet and change the scaling to powersave.

In Karmic 9.10 it was set to Powersave by default.
In Lucid 10.04 it's set to Ondemand by default.

Since Ondemand allows the CPU to speed up it creates more heat.
That's what the cause was on my laptop.
:popcorn:

---

### Post by cimh on 2010-05-15
> **2hot6ft2 said:**
> Right click on the top panel and select Add to Panel.
Select CPU Frequency Scaling Monitor.

Thanks, powersave is worth using, as I do all the time (I use jupiter to switch). The trouble is that powersave changes cpu speed according to demand and in my lucid install demand is so high that powersave cannot drop the cpu down to the lower speeds. Although in unr it is able to do this, so in my case its something in the standard version that isnt in unr.

cimh
eeepc 901, lucid, lubuntu, unr, puppeee

---

### Post by request_another on 2010-05-15
I also experience high temperatures on ubuntu 10.04. With the laptop set to performance i get a solid 70 degrees, and on ondemand i get 60 degrees.

The problem is that while im booted into windows 7, on performance mode i get 52 degrees, a whole 18 degrees lower, and quieter fans too. And on power save i get 48 degrees. This is a big annoyance really. I dont want to keep it on Ondemand because i want the full power of my laptop available to me.

Could this issue be fixed by an update?

---

### Post by cimh on 2010-05-15
I think this is the bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156?comments=all)

if you agree then perhaps you would report it. That's what I have done - the more people that do - I guess the more likely it is to get fixed.

cimh

---

### Post by camdude on 2010-05-15
I've never had a problem with temperature with Ubuntu, believe it or not, my laptop is actually running cooler than it did in Fedora 12! However, depending on your hard drive speed, and the amount of RAM you have, and your CPU speed, the fan could be on more.
The loud noise is definitely the fan running constantly... You might try looking in your BIOS for fan settings, or disabling the OS from overriding your power/fan settings (that would be in BIOS too)... if that doesn't work, that it's a bug

---

### Post by anantshri on 2010-06-11
hope i am not bumping an old thread but just my two cents.


With Radeon drivers the CPU temp at my system is 58 degree idle.
and battery time fully charged is close to 3 hrs.

but with flgrx drivers the CPU temp at my system is 48 degree idle. and battery time fully charged is close to 4:30 - 5:00 Hrs


I have a 9 cell battery. and using Ubuntu Lucid x64 edition.



also on a side note my Windows 7 with 64 bit gives me a temp range of 42 degree with 5:30 - 6:00 hrs of battery backup.

---

