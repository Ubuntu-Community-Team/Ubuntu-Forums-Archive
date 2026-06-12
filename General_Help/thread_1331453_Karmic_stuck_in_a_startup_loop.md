---
title: "Karmic stuck in a startup loop?"
date: 2009-11-19
forum: General Help
---

### Post by cybrsaylr on 2009-11-19
KK 64 bit runs great on my laptop.
Installed KK 32 bit in my older desktop and set it to automatically login like my laptop. However my desktop always makes me login at least 2 times! Today it looped around and made me login 4 times before letting me in!
I did a clean install with the KK Live-CD ShipIt sent me.

How do I correct this so it just logs in like before, with all other versions I've used since FF?

---

### Post by Progressive on 2009-11-19
I have the same problem as of last night.... though I am using 64 bit and haven't been able to log in at all. I haven't tried to log in 4 times though... perhaps that will let me in

tried installing gnome, turning off kms, downgrading from xorg-edgers to the regular repositories, etc. Nothing seems to work, so I am assuming it is a problem with the Main repository.

I'm forced to use xterm right now.

---

### Post by cybrsaylr on 2009-11-19
My laptop starts and will shutdown normal running 64 bit KK.

However not with my desktop running 32 bit KK.
Besides making me login multiple times before KK lets me in, when I shutdown it won't shut off the PC completely. It shuts down KK then goes to a black DOS-like screen with cursor blinking but still power and fan is running. I have to hit the power button to completely shut the PC off.

---

### Post by efflandt on 2009-11-19
If you can get into xterm or a console (Ctrl-Alt-Fn where n is 2 to 6), try reviewing **dmesg | less** or various logs in /var/log (including /var/log/messages) to see if they reveal any issues.  Xfce login issues I had with Xubuntu 9.10 on an old PC after updating packages appears to be due to drive errors (unable to read some sectors), but I could still log into xterm or console.

---

### Post by Progressive on 2009-11-19
Turns out for me the problem is that compositing is failing. I turned it off via Gnome Failsafe mode (for GNOME and KDE) and now I can log into both.

---

### Post by cybrsaylr on 2009-11-20
Any idea how to fix this?

Today it took 7 tries before I could get into KK.
This is pretty annoying.
My laptop starts KK with auto login with no problem. It's just my desktop that keeps looping around repeatedly asking me to login.

---

### Post by cybrsaylr on 2009-11-23
Got lucky today. Only took 3 times to login before it let me in.

Anyone got any ideas how to get KK to auto login?

---

### Post by ikacer on 2009-11-23
I am experiencing what *may* be the same bug. For me logging in fails and goes back to the log in screen. From my syslog at the time of the failure, I have
```
gdm-simple-slave[3697]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory

```
Here is my thread on the problem: [http://ubuntuforums.org/showthread.php?t=1334740]("http://ubuntuforums.org/showthread.php?t=1334740")
As of yet, I still haven't found a solution to the problem, although using "failsafe GNOME" as my session allows me to log in.

EDIT: turns out my bug was unrelated to the one on this thread. mine was caused by changes in ~/.profile.

---

### Post by cybrsaylr on 2009-11-24
ikacer,
I tried a couple solutions on your thread with no luck.
Even created a new user and it auto booted once completely, then when tried again it started to loop around again repeatedly asking for the password a couple times before letting me in. 

My desktop just goes through too many pages on boot up compared to my laptop that just auto logs in as normal. Desktop is very annoying.

---

### Post by ikacer on 2009-11-24
I suggest you take a look at your log files (/var/log/), which may give a better idea of what is happening. Two which might be important are:

/var/log/auth.log
/var/log/syslog

The entries have timestamps on the left so you should be able to find a range of warnings, errors, etc. which happen during the failed logins. If you post those, people might have a better idea of how to help.

---

### Post by cybrsaylr on 2009-11-25
> **ikacer said:**
> I suggest you take a look at your log files (/var/log/), which may give a better idea of what is happening. Two which might be important are:

/var/log/auth.log
/var/log/syslog

How do I find them?
Went through System > Administration > Log File Viewer but couldn't find them.

BTW today KK almost auto booted with having to put the password in only 1 time. Still it goes into a black shut off screen a couple times and a couple other pages that my laptop doesn't go through when booting up.

---

### Post by ikacer on 2009-11-25
> **cybrsaylr said:**
> How do I find them?
Went through System > Administration > Log File Viewer but couldn't find them.

BTW today KK almost auto booted with having to put the password in only 1 time. Still it goes into a black shut off screen a couple times and a couple other pages that my laptop doesn't go through when booting up.

In the log file viewer there should be a column  of files on the far left. Select "syslog". From there, just look for the ones which have time stamps from when your problems were happening.

---

### Post by cybrsaylr on 2009-11-27
Well I think I solved the problem...... got a new PC!

I suspect it's 32 bit KK. 
Installed 64 bit on my new Dell with an i7-860 CPU and it boots up normal, just like my Toshiba laptop running 64 bit KK also.

FWIW,
Only had trouble with that loop booting up with 32 bit KK.

BTW the new PC flys! Fastest PC owned do far. Took 30 minutes to install 64 bit KK including 137 updates after the install! That i7 CPU is FAST! It's a dual boot setup with Windows 7 and KK.

---

### Post by asdeasde on 2009-11-29
I had the same problem
 

 it was that the resolution of the login screen (higher) was not the same that the  
 desktop screen that I set up (lower)
 

 the installation default was 1280x960 I changed to 1152x864 this was causing 

 the login loop 

 

  now it is back to 1280x960  
 

 I think that the different resolutions login (higher) and 

 desktop (lower) cause the loop
  

 when the login screen goes to the desktop it change resolution 

but it dos not go to the desktop it goes back to the login  
 

 this work for me I hope it works for you  
 

 try to set the same resolution on both screens, from the recovery mode   
 

 does anybody knows were the config files for the login and the desktop screens are? 

 

            
pd English it is not my native language

---

### Post by asdeasde on 2009-11-29
several logins and working great

---

### Post by cybrsaylr on 2009-11-29
Interesting because the installation default was 1280x960 for me and I changed to to one lower than 1152x864 but never thought that caused the login loop. Don't know why this would cause the loop because I've changed resolutions in the past and never had this kind of problem.

---

### Post by Chimmer on 2009-11-29
> **cybrsaylr said:**
> Interesting because the installation default was 1280x960 for me and I changed to to one lower than 1152x864 but never thought that caused the login loop. Don't know why this would cause the loop because I've changed resolutions in the past and never had this kind of problem.

See [this post]("http://ubuntuforums.org/showpost.php?p=8408929&postcount=18") in a similar thread that I started. I have an old CRT monitor and it worked fine until a recent -15 ubuntu image update and then I got caught in the login loop.

One thing I noticed was that my login resolution was set too high, everything wouldn't fit on the screen. Every now and then I was able to login to ubuntu and my desktop resolution was 1024x768 but the login screen resolution was set higher than that.

I suspected that may have been causing issues so I edited the xorg.conf file so that my login screen resolution was now 1024x768. So far I've logged in successfully at least 8 times so I think this fixed the login loop issue for me.

---

### Post by cybrsaylr on 2009-11-30
> **Chimmer said:**
> One thing I noticed was that my login resolution was set too high, everything wouldn't fit on the screen. Every now and then I was able to login to ubuntu and my desktop resolution was 1024x768 but the login screen resolution was set higher than that.

That's the resolution I preferred but never thought it was causing the login loop on my CRT monitor. Anyways the new PC seems to have solved my problem and KK now auto boots in 40 seconds.

---

### Post by cybrsaylr on 2010-05-24
> **Chimmer said:**
> One thing I noticed was that my login resolution was set too high, everything wouldn't fit on the screen. Every now and then I was able to login to ubuntu and my desktop resolution was 1024x768 but the login screen resolution was set higher than that.

Was playing around with this PC again. It is still stuck in the login loop, took about 7 trys before it let me in. Am using the 1024x768 resolution and it still loops at login.

Anyone figure this one out yet?

---

### Post by dino99 on 2010-05-24
you might find some usefull info into .xsession-errors or logs (user, system)

but check your keyboard prefs (hardware model and other settings)

---

### Post by cybrsaylr on 2010-05-25
Just installed 32 bit Lucid on this PC and Lucid starts up with no problems.

This PC now has a triple boot on it now. 
XP Pro, Karmic and Lucid.
I only have this login loop problem with 32 bit Karmic.
Last time it took 8 attempts before it let me in Karmic.

---

### Post by dino99 on 2010-05-25
sudo dpkg-reconfigure gdm

---

