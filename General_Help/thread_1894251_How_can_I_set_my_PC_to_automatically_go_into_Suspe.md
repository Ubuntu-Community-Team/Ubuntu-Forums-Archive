---
title: "How can I set my PC to automatically go into Suspend mode if it's idle for 2-3 hours"
date: 2011-12-12
forum: General Help
---

### Post by oscarivera9 on 2011-12-12
Prior to the Ubuntu 11.10 release, I was able to set my PC to automatically go into Suspend or Shutdown after being idle for 2-3 hours.  Now, the Power Settings have fewer choices than before.  On my desktop, I only have the option to go into Suspend mode after being inactive for 5, 10, 30, or 60 minutes.  There are no other choices available to me.  The only other choice given is to put a laptop into either Suspend or Hibernate when power is low, but since I'm not using a laptop, that choice doesn't really apply to me.
I imagine there's got to be a way to set the computer to Suspend for longer times than the ones given, but I don't know how to do that.

Thanks in advance for your help

---

### Post by spiky001 on 2011-12-12
I,m not on 11.04  at the moment, Have a look in preferences power managment

---

### Post by lechien73 on 2011-12-12
Yes, the System Settings -> Power applet really does seem to be limited in the options for hibernation.

I haven't tested this, but you could try opening a terminal window and running:

```
dconf-editor
```

When dconf-editor is open, navigate to **org -> gnome -> settings-daemon -> plugins -> power**

Change the **sleep-inactive-ac-timeout** and/or **sleep-inactive-battery-timeout** to the number of seconds you want (e.g. 10800 for 3 hours). Make sure that the **sleep-inactive-ac** and/or **sleep-inactive-battery** boxes are checked as active.

Quit from dconf-editor and wait :) You may have to log out and back in again to refresh the dconf settings.

---

### Post by oscarivera9 on 2011-12-13
> **lechien73 said:**
> Yes, the System Settings -> Power applet really does seem to be limited in the options for hibernation.

I haven't tested this, but you could try opening a terminal window and running:

```
dconf-editor
```When dconf-editor is open, navigate to **org -> gnome -> settings-daemon -> plugins -> power**

Change the **sleep-inactive-ac-timeout** and/or **sleep-inactive-battery-timeout** to the number of seconds you want (e.g. 10800 for 3 hours). Make sure that the **sleep-inactive-ac** and/or **sleep-inactive-battery** boxes are checked as active.

Quit from dconf-editor and wait :) You may have to log out and back in again to refresh the dconf settings.
Thanks lechien73
I followed your instructions, now I guess I wait to see if my PC goes into Suspend mode in 2 hours.
I'll post again after I know the true outcome.

---

### Post by oscarivera9 on 2011-12-25
Thanks for the help, lechien73, it worked just fine.  All I had to do was follow your advice and then wait until I noticed that it worked.  I am now a happy camper with my old Power settings the way I had them on Ubuntu 11.04 and older.
Way cool!
I still wish there was an easier way to go about it, like in the old days.  Maybe in 12.04 we can revert back to the old menu with more options and flexibility.   
):P

---

### Post by oscarivera9 on 2012-04-28
> **oscarivera9 said:**
> Thanks for the help, lechien73, it worked just fine.  All I had to do was follow your advice and then wait until I noticed that it worked.  I am now a happy camper with my old Power settings the way I had them on Ubuntu 11.04 and older.
Way cool!
I still wish there was an easier way to go about it, like in the old days.  Maybe in 12.04 we can revert back to the old menu with more options and flexibility.   


.......well, here we are four months later, 12.04 has been released and it seems like the old power flexibility from before 11.10 has not come back.  What a bummer...:sad:
    What's worse, I tried to check to make sure that the settings I had previously changed were still in effect and apparently the dconf-editor needs to be installed because it is no longer available by default.  I assume dconf-editor is just an editor so again I will wait a couple of hours to see if my previous settings have changed.  I just upgraded to 12.04 today (pretty flawlessly :p) and I am just testing the whole system for any changes, both positive and negative. 
   I will post the results here when I have an answer.

---

### Post by oscarivera9 on 2012-04-30
[FONT=Comic Sans MS][SIZE=3]My PC is still going into suspend mode after two hours!!![/SIZE][/FONT]
=D>

---

### Post by linuxgeoff on 2012-05-01
glad it worked.  I've just bee through the same insanity loop, including re-enabling hibernation.  It's getting harder to love ubuntu.  An update really should not require the user to start hacking configuration files in order to get their machine to behave the way it did before the upgrade.  This is why, unfortunately, Linux use will be limited to nerds and geeks (IMHO!)! I know that my wife and kids could never use Linux without me in the house, but with windows and apple - no problem!

---

### Post by oscarivera9 on 2012-05-01
> **linuxgeoff said:**
>   An update really should not require the user to start hacking configuration files in order to get their machine to behave the way it did before the upgrade. 

I completely agree!!!

By the way, remember that you may have to install dconf-editor as it is ***no longer included in Ubuntu 12.04, ***but it IS available, I checked.

---

