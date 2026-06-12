---
title: "Ubuntu karmic 9.10 stand by issue"
date: 2009-11-27
forum: General Help
---

### Post by nicoalmontec on 2009-11-27
Greetings to all, my name is nicolas, this is my first post on this forum. I am a beginner Ubuntu user, the first version I used was 8.10. I also use windows. this is a very stabe, friendly and safe system and I would recomend it to anyone.

However I got this problem with my netbook:

First of all these are the basic Specs about my netbook:
Acer AspireOne 10.1"
Intel Atom processor 1.60 GHZ
1 GB RAM
64 MB integrated graphic.
160 GB hard drive.
Simplo 4-cell battery

I  upgraded to ubuntu 9.10 since it was released, what happens is the following:

1-If im running on batteries, the system would switch to stand-by as soon as I connect the power cord, and the same happens backwards: I im running on AC and I unplug the power cord, the system would switch over to stand-by.

2-When I switch over to windows, it doesnt happen anymore, I conclude there is something on Ununtu that is causing the problem.

I've been reading posts for a while now but I havent found any help for this problem.

I would really appreciate  if any of you can give me some feedback on this.

thank you in advance.

---

### Post by nicoalmontec on 2009-11-27
[COLOR="DarkOrange"]I forgot to say I have a friend that has this same Acer AspireOne and he is also having  the same issue.[/COLOR]

---

### Post by staf0048 on 2009-11-27
Have you tried different settings under the power manager?

It's under System/Preference(I think)/Power Manger.  Should have several options there, try setting it to "do nothing" and see what happens.  That should at least help you determine if that's the cuase of your trouble.

*Edit - sorry I should be a little more helpful.  I'm on an XP machine here at work, so just going off of memory.  There are several settings for AC power and battery power, set them to the same settings, like max performance, and see if you still have the same problems.*

---

### Post by nicoalmontec on 2009-11-27
Ok, Im going to go back to ubuntu and check one more time, dont go too far fella!!

---

### Post by nicoalmontec on 2009-11-27
I went to power management preferences and tried all possible combination of settings, but no go.

---

### Post by staf0048 on 2009-11-27
Did you have a previous version on this same computer before the trouble started happening?

I ask this because I've personally found 9.10 to be a little too buggy (I had major "suspend" issues) and everything from 9.04 and back has worked great on my computers.  I'm not sure what is going on with your computer, but you might want to try a live cd/usb of a different version and see if that fixes your problem.  It's very strange...

Probably not what you want to hear and maybe someone else has a better idea, but aside from power management settings, I'm stumped on this one.

---

### Post by nicoalmontec on 2009-11-27
Its kind of dummy, but I did not remember this was a netbook, they dont have cd room or dvd, everything works via USB on this.. so there arent many options for me now...:s

---

### Post by jdent on 2009-12-15
I'm having the same issue with 9.10 on my Dell Inspiron 700m laptop.  Right now I'm not getting my hopes up for a fix (since it is nearly 5 years old), but it's nice to hear that the issue isn't isolated to my machine.. maybe someone will figure something out.

---

### Post by DarkManX4lf on 2009-12-20
Same issue here.  I have a Dell 700m and if I have ubuntu running with the ac adapter plugged in and unplug the ac adapter the computer automatically goes into standby. If I turn on the computer once it would turn on and go right back into stand by.  I would have to turn it on the escond time for the computer to actually work.

---

### Post by ludditic on 2009-12-23
I can confirm this bug on my installation of 9.10 as well. Weird thing about it is mine is also a Dell 700m. Same exact symtoms:
   Running on AC>unplug cable>goes to standby
   Running on Battery>plug in ac cable>goes into standby.
I thought it was my battery, as this lt is old, and the battery is end of life. It keeps a charge for a bout 7 minutes. I have a new extended life batt coming hopefully tomorrow. :)
 
This is more of an annoyance than anything. I am a complet newb, and am fairly smitten with ubuntu already:P

---

### Post by junapp on 2009-12-23
> **DarkManX4lf said:**
>  If I turn on the computer once it would turn on and go right back into stand by.  I would have to turn it on the escond time for the computer to actually work.

Interesting. I have my laptop set to suspend when the lid is closed. Once I open it back up, I come out of suspend, get the prompt for my password which I cannot type in. I have to hit the power button, which seems to shut it off for a second and bring it out of suspend again, this time allowing me to type in my password. This is on a Dell Studio 17"

@nic: you should be able to create a live cd on a usb stick if you want to test the live cd behaviour.
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by jdent on 2009-12-23
So I was experiencing this issue as described in the above post #10 (with my 700m), but after playing around with some settings, I realized that if you turn your brightness to max on battery power, then plug in the ac adapter, it doesn't to trigger the standby.  However, removing the ac adapter will cause a standby response regardless of the backlight settings.  This at least eliminates the annoyance of plugging in the ac adapter while the computer is running.

---

### Post by ludditic on 2009-12-24
I think i am going crazy. The symptoms i described have stopped. I can plug/unplug the ac cord at will w/out affect. Weird. The only recent change is that I installed emerald. That can't be it, can it?

---

### Post by maxrpowell on 2009-12-24
In the 'running on battery tab' of 'power management' there should be an entry called 'when battery power is critical' change it to 'Do Nothing' instead of 'Suspend'. Hope it works for you guys.

---

### Post by ludditic on 2009-12-24
Disregard, it is still happening. Got my new batt today and have seen it happen with unplugging the ac cord, but not consistently.  So far though, when running on batt and plugging in cord, it has not happened.

---

### Post by ludditic on 2009-12-24
> **maxrpowell said:**
> In the 'running on battery tab' of 'power management' there should be an entry called 'when battery power is critical' change it to 'Do Nothing' instead of 'Suspend'. Hope it works for you guys.
maxrpowell
Where are you seeing 'Do Nothing', all I have in the area you referred to is: Suspend, hibernate, shutdown...?

---

### Post by jdent on 2009-12-24
Alright guys, I think i figured out a work-around..

On the power management, under the 'on battery power' tab, just set 'When lid is closed' to BLANK SCREEEN instead of SUSPEND.

Now I just get a blank screen and can get it to come back by moving the mouse instead of having to get out of standby.

This seems to fix the annoyance of removing the ac adapter.  For some reason I'm not having problems plugging in the adapter either now.  :)


-- Can anyone tell why unplugging my ac adapter triggers a 'closing lid' response??

---

### Post by schmolch on 2009-12-24
-Run gpm (gnome-power-manager) in verbose-mode. This way you can see exactly what is going on.
-Update gpm to its latest version from cvs.
-Contact the developers on their mailing-list of you still have problems.

---

### Post by ludditic on 2009-12-24
> **jdent said:**
> Alright guys, I think i figured out a work-around..

On the power management, under the 'on battery power' tab, just set 'When lid is closed' to BLANK SCREEEN instead of SUSPEND.

Now I just get a blank screen and can get it to come back by moving the mouse instead of having to get out of standby.

This seems to fix the annoyance of removing the ac adapter.  For some reason I'm not having problems plugging in the adapter either now.  :)


-- Can anyone tell why unplugging my ac adapter triggers a 'closing lid' response??
Thanks for the tip jdent! Bailing wire and duct tape, but it beats the alternative...

---

### Post by Pluto1010 on 2010-01-14
I can also confirm this bug on my Samsung X20 1600 III.. The Blankscreen on lid-close helped me too. Has anything new happend to this till now? I'm waiting for an update. 

I installed 9.10 (previous 8.04) to get firefox 3.5 and I got new problems for free! Impressive ;)

---

### Post by dbenzhuser on 2010-01-14
Same happening with my Samsung X20 1600 II.

---

### Post by inigopete on 2010-01-15
FWIW, same happening on my Dell Mini 10v netbook. If I change the charging status, it does the same action that I've selected for closing the lid. Although, frustratingly, not every time!

It's also stopped prompting me for a password when I resume from standby.

---

### Post by energystar on 2010-02-11
Hi all,

I am experiencing this slight irritation. Thanks for the workaround of changing the settings to Blank Screen.

running 9.10 netbook remix on a hp mini 1001TU.

i don't mind too much but it would be nice to get a fix. :)

---

### Post by bama7474 on 2010-02-20
Having same problem with my Toshiba NB305 -N410BL...can't suspend, come out of suspend with a black screen with no backlight...status lights indicate it has resumed but screen does not come back, Hibernate doesn't work either...I followed the advice of others on here to just put close lid to black screen and it works but doesn't cut back on power usage, but wish they would come up with a way to fix suspend and hibernate functions...netbooks are designed to be mobile so you'd think that UNR, which is designed for a netbook, would have thought about this function first.  Looking forward to a fix, guess I'll keep googling like everyone else...:confused:

---

### Post by craigester on 2010-03-20
My machine is an AMD 64 bit desktop with 9.10. I put in a new AGP Nvidia graphics card (Geforce 7300GT) and since that time I have been struggling with a nasty problem that the screen goes into standby mode randomly, but often after or at login. I then restart X server (Ctrl Alt Back) and that sometimes solves it. Otherwise I have to restart multiple times. I installed the newest proprietrary nvidia drivers from the nvidia repos. I have checked the xorg conf file and log files for Xserver and there is nothing wrong apparently.

At the moment I am really disillusioned about Ubuntu as this problem means the PC is unusable for a lot of the time and I don't have the patience to fiddle with it every time I want to use it.  There have been some kernal patches recently but these have not solved this.

Is this even the same problem as on this thread?  If not please excuse me.

---

### Post by lrbradford on 2010-04-05
I've had this main problem since I did an update to 9.10. I'm running an HP Pavilion dv1000.  If I'm on the laptop, and deside to move to another room on battery, in a matter of a few minutes, the laptop goes into a hibernate (I assume), power button is the only light on, and the light flashes, screen blank and if I press the power button, it comes up with a login screen.  Very annoying problem, Ubuntu gurus!;)

I've modified the power management to the suggestions here, so I'll see if the problem goes away, or turns into something else that is annoying.

Thanks for noticing me...
:guitar:

---

