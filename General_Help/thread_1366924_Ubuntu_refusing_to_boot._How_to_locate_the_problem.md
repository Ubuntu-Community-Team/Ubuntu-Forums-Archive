---
title: "Ubuntu refusing to boot. How to locate the problem and fix it?"
date: 2009-12-28
forum: General Help
---

### Post by Charkel on 2009-12-28
Hello. A few minutes ago I started my computer and tried to boot Ubuntu, but apparently it doesn't wanna boot. :cry: The first thing I noticed was that the ubuntu logo stayed for way too long and then everything went black. I was waiting for it to go into X but nothing ever came up. It just stayed black. It wasn't a commandline or anything, just black. That's what usually happends but only for a few seconds before the login screen appears. But it never continued.
I can boot into safe mode but I have no idea what to do there.

Please help, I wanna get back into ubuntu. Windows is such a pain in the a** ](*,)

EDIT:
[http://img14.imageshack.us/img14/4146/dsc04015j.jpg](http://img14.imageshack.us/img14/4146/dsc04015j.jpg)

SOLVED!
Used this tutorial from a liveCD
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)

---

### Post by Sef on 2009-12-29
What version are you running?

Have you tried booting into safe mode?

---

### Post by Charkel on 2009-12-29
> **Sef said:**
> What version are you running?

Have you tried booting into safe mode?

9.10 and yes I can boot into safe mode but that's just a terminal. Or should it contain a GUI?

---

### Post by oldfred on 2009-12-29
No it should be a terminal so you can do updates. Did you change or update your video card or driver? It sounds like a video issue. 

If there is anything to automatically update
sudo apt-get update 
sudo apt-get upgrade 

startx
 will start the gui if it will work.

---

### Post by Charkel on 2009-12-29
> **oldfred said:**
> No it should be a terminal so you can do updates. Did you change or update your video card or driver? It sounds like a video issue. 

If there is anything to automatically update
sudo apt-get update 
sudo apt-get upgrade 

startx
 will start the gui if it will work.

The only thing i did last time I was on Ubuntu was this:
```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

And uninstalling some flashplugins.

---

### Post by MelDJ on 2009-12-29
what happens if you type startx?

---

### Post by Charkel on 2009-12-29
> **MelDJ said:**
> what happens if you type startx?

I will try that now before I go to bed and see what happens. If it works and I can start a browser I'll write here. Else I will check this thread later today.

Thank you.

---

### Post by Charkel on 2009-12-29
Got back into Windows a quickie to show you the results. Since I cannot printscreen I took a picture:

[img]http://img694.imageshack.us/img694/4146/dsc04015j.jpg[/img]

It didn't recognize the commands and there's some "Alert"

I cross my fingers hoping someone knows what's upp. Will check back in a few hours.

Thank you

---

### Post by MelDJ on 2009-12-29
try running a chkdsk /f from windows. then boot cleanly into ubuntu

---

### Post by Charkel on 2009-12-29
> **MelDJ said:**
> try running a chkdsk /f from windows. then boot cleanly into ubuntu

It only tries to check the Windows NFTS partition.

---

### Post by MelDJ on 2009-12-29
how did you install ubuntu? on its on partition/wubi?

---

### Post by Charkel on 2009-12-29
> **MelDJ said:**
> how did you install ubuntu? on its on partition/wubi?

Got it working now :D Googled the "ALERT!" error and found this:
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
Used a LiveCD 

Back in Ubuntu now. Phew.
I wonder how this just suddenly happaned tho :\

---

