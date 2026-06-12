---
title: "Need help with several issues"
date: 2011-09-17
forum: General Help
---

### Post by Exavior on 2011-09-17
I apologize for my noob-ism in advance. I'm usually the person that people go to for help but I'm entirely new to linux (I'm sure you hear that a lot). Anyhow, My windows recently crashed and I've turned to Ubuntu linux. I really love it and I have no idea why I haven't managed to tear away from windows before now. So, here are some issues I could REALLY use some help with.. 

    I'm assuming I have the most up to date version of Ubuntu since I downloaded it from the site just a few days ago but here's my list of, issues. 

    Starting up ubuntu the login screen and graphics appear flawless. But when I choose ubuntu (normal mode) it starts up, everything appears great for a split second and then poof, a strange graphical “overlay?” seems to distort my entire screen. I thought this might be gnome related but it also comes up when I open ubuntu classic? If I restart my system several times (20 or so times) it will eventually open  and function all appearing good and normal. Also, if I open ubuntu in safe mode it always appears fine. 

    I's frustrating because like I said if I keep restarting it eventually will appear correctly, so I know it can.  What's different about how it starts up and runs one time than the next? How can I fix it? I like the interface and would prefer not to have to work in safe mode. 

    Second, ubuntu doesn't always start on boot-up at all. Sometimes I choose to start ubuntu and often get hung at a message saying mmoi address already in use. 

    Third, and this is my probably my own stupidity. Is it safe to delete the old boot.ini in my main drive? I typically have to choose either windows (broken) or ubuntu from this list. Then choose what ubuntu I want to run from the ubuntu startup. 

    I would appreciate it truly if someone could help me with any of these issues.

---

### Post by varunendra on 2011-09-18
Hello Exavior, and welcome to the forums :)

First problem of yours seems (quite certainly) related with inappropriate driver for the graphics adapter:
> **Exavior said:**
> Starting up ubuntu the login screen and graphics appear flawless. But when I choose ubuntu (normal mode) it starts up, everything appears great for a split second and then poof, [COLOR=Red]**a strange graphical “overlay?” seems to distort my entire screen**[/COLOR]. I thought this might be gnome related but it also comes up when I open ubuntu classic? If I restart my system several times (20 or so times) it will eventually open  and function all appearing good and normal. Also, [COLOR=Red]**if I open ubuntu in safe mode it always appears fine**[/COLOR]. 
As a first attempt, boot into safe graphics mode, get connected to Internet, then from under "System Settings", open "Additional Drivers" application and see if a suitable driver for your graphics is listed in it. If there is any, enable it and restart in normal mode to see if it gets better.

If no driver is listed, or enabling a proposed one doesn't help, then we'll need more info about your system to proceed further. Accordingly, please post the specs of your computer, especially amount of RAM. For graphics adapter details, as well as driver currently associated with it, open a terminal, enter the following command and post back its output here:
```
sudo lshw -C display
```

Your second problem may probably be solved automatically once we get the graphics issue resolved. So, onto your third question-

    > **Exavior said:**
> Is it safe to delete the old boot.ini in my main drive? I typically have to choose either windows (broken) or ubuntu from this list. Then choose what ubuntu I want to run from the ubuntu startup....
The boot.ini file holds boot parameters info to boot Win XP. If you delete it, you will no longer be able to boot XP (try renaming the file from within Ubuntu and see the effect yourself). If you don't want to use XP, which you say is already broken, then deleting it or anything in windows partition will have no effect on Ubuntu installation. So if you want to get rid of it, you can safely delete even the entire partition of windows.

As for 'which Ubuntu' to boot, as you have already figured out, the recovery mode is for what it is named as - for recovery and repairing. For normal login, boot into default Ubuntu. But currently you may keep using the recovery mode until the graphics issue is resolved.

---

