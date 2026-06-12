---
title: "Ubuntu 10 messing with my System Time"
date: 2010-11-08
forum: General Help
---

### Post by kakashi_12 on 2010-11-08
Here's the deal. My time kept screwing up. No matter what OS I was in and in the BIOS. I would fix the time in all the OS's and then it would change back anyway. The time actually jumps AHEAD, not falls behind. I replaced the CMOS battery!
 
That did not do anything. I reset the time with the new battery in the BIOS. Then set the time in the OS's. Here's the catch...
When I set the time in Windows and/or in BIOS, I'm fine. The time stays.
When I change the time in Linux and reboot, CMOS and Windows time are messed up again (jumping to tomorrow's time).
I KNOW, BECAUSE I tried once NOT changing the time in Linux, Rebooting, and the times in BIOS and Windows stayed the same.
 
What the deal!?

---

### Post by kakashi_12 on 2010-11-08
btw, I always have 'time sync' turned off. It never works right with the time zone.
Also, I currently have no internet at my place yet. Is linux required to be online to keep time? I wouldn't think so. But the fact that I change it screws everything else up, gets me.

---

### Post by efflandt on 2010-11-08
**man hwclock**

Usually Linux will tend to use UTC for the CMOS clock/calendar (hardware clock) unless it recognizes that it is localtime (which Windows uses).  But depending upon how things were set during installation or afterwards, Linux might not realize that the clock/calendar should be localtime, so it sets it to UTC time.  I think the following should correct that as long as your system time is showing the correct time (which works best automatically getting time from time servers):

```
sudo hwclock -w --localtime
```

See [http://www.linux.org/docs/ldp/howto/Clock-2.html](http://www.linux.org/docs/ldp/howto/Clock-2.html)

---

### Post by kakashi_12 on 2010-11-08
do i have to be online for that? currently have no internet (on that pc). i'll have to hok it up somewhere else unless there is another solution.
i'm on wifi on laptop now.

will that change the UTC setting?

---

### Post by kakashi_12 on 2010-12-26
Ok, I FINALLY have internet access now. This still IS NOT working!
 
I have ran the code above. This time, when I boot into Linux, I do NOT change the time, it is already set correctly. BUT then when I reboot into Windows the time goes ahead 5 hours. I can go into the "internet sync time settings" and re-sync it. BUT then I would have to reset it EVERY time I use Linux. 
 
What is the resolution for this?!

---

### Post by ManyBeers on 2010-12-26
> **kakashi_12 said:**
> Ok, I FINALLY have internet access now. This still IS NOT working!
 
I have ran the code above. This time, when I boot into Linux, I do NOT change the time, it is already set correctly. BUT then when I reboot into Windows the time goes ahead 5 hours. I can go into the "internet sync time settings" and re-sync it. BUT then I would have to reset it EVERY time I use Linux. 
 
What is the resolution for this?!

I dual boot Win7 and Ubuntu 10.04 and I avoid the problem by booting into Windows and let it set the time via one of it's Internet time servers. Once Windows has the correct time boot into ubuntu and in it's time and date settings disable update time via Internet(there is a setting in there where Ubuntu will use the local machine time). Basically you want either Windows or Ubuntu to set the time and the other to follow. You can have Ubuntu setting the time via Internet and then let Windows use the machine time but it is more difficult to do. Both my Win7 and Ubuntu 10.04 installs show the correct time no matter which system I am booted into.

Incidentally I let Win7 run the show because I use it far more frequently than Ubuntu. If you are using Ubuntu more 
maybe you'll need to find the info on forcing Windows to use UTC time. It can be done because i have seen the tutorial on it.
[Registry edit for Windows]("https://help.ubuntu.com/community/UbuntuTime#head-31a2e864837bce9761bc0520026f78970d18afde")

---

### Post by kakashi_12 on 2010-12-26
i dont see a setting. i see "set system time", thats wont help.

---

### Post by ManyBeers on 2010-12-26
> **kakashi_12 said:**
> i dont see a setting. i see "set system time", thats wont help.

I'm on Ubuntu 10.04. Go to Main Menu... System...Administrstion..
Time and Date in the configuration field set it to Manual.
In other words unlock it set the correct time and leave it on manual.

---

### Post by kakashi_12 on 2010-12-26
Found the settting, but still not working!
I opened it and it was already set at Manual. Therefore it has been all along. I tried the other setting then, Sync to server, and selected one in my state to sync to. I have also tried turning off the sync in Windows. Nothing is working here. Every time I boot into Linux and then reboot into Windows, Windows time always screws up! still.

---

### Post by kakashi_12 on 2010-12-26
I found the setting. But it did not help. It was already set to Manual. Therefore it has been all along. I tried the sync to server setting and selected a server near me. I also tried turning off sync in windows. that STILL did not work! grrrr. I also tried faking windows time by switching the time zone 5 hours behind me so that it would not jump 5 hours ahead. BUT that still did not work!!! No matter what, after booting into Ubuntu, then rebooting to Win, the time still goes 5 hrs ahead in win! Even both set to manual and sync off.

---

### Post by ManyBeers on 2010-12-26
> **kakashi_12 said:**
> Found the settting, but still not working!
I opened it and it was already set at Manual. Therefore it has been all along. I tried the other setting then, Sync to server, and selected one in my state to sync to. I have also tried turning off the sync in Windows. Nothing is working here. Every time I boot into Linux and then reboot into Windows, Windows time always screws up! still.

Leave Internet sync on in Windows. You want Windows to set the system clock via it's Internet time servers and Ubuntu will simply use the system clocks time. Go online in Windows and make sure it updates the time through one of the Internet time servers. Then unhook your Internet cable or wireless card and boot Ubuntu, it should show the correct time.

Sorry there is one more thing you need to do.

Open a terminal and 
enter sudo gedit /etc/default/rcS
when the file opens change the UTC=entry from yes to no
That tells Ubuntu to use local time.

M[y own thread on the problem]("http://ubuntuforums.org/showthread.php?t=1393813")

---

### Post by kakashi_12 on 2010-12-27
Hallelujah! Finally! Thank you for that fix.

---

### Post by kakashi_12 on 2011-09-24
So guess what! :D

I just had my Motherboard RMA'd due to problems with it. When I got the new Motherboard, I did not have to set any of the settings above! I just did a normal install, set the time in the BIOS, and wall-a! No problems with the time and either OS.

Found out that it was the faulty motherboard that was giving me problems! Not linux.
Bad Asus, bad!

---

