---
title: "Skype does not start in Natty"
date: 2011-05-26
forum: General Help
---

### Post by asv1988 on 2011-05-26
Hey guys,

So I have a problem. Today in the morning I did update my system and my skype does not start anymore. Thiugh I am not sure if this is related to my new update(May 26), because it was in the morning and I didn't see if my skype was on/off. But definitely it doesn't work now. The first thing I tried was to uninstall and then reinstalling skype. It opens but when it tries to load the user(mine is set to automatically load user when skype starts) it just shuts down. I tried logging out. rebooting and shutting down my laptop. nothing works. And it used to work before without any problems.

Any ideas/thoughts/suggestions?

I am running fresh install of Ubuntu 11.04, and skype beta 2.2

---

### Post by asv1988 on 2011-05-26
Oh never mind. It seems that this is what causes the problem:

[B]Skype hit by Global Service Crash.
[/B]

**[http://www.bbc.co.uk/news/technology-13565864](http://www.bbc.co.uk/news/technology-13565864)**

Lol, I guess that's what we get when something is run by microsoft. too bad

---

### Post by fcrvincent on 2011-05-26
Same problem here with Ubuntu LTS 10.04 Lucid. 
Until yesterday Skype started and worked fine.
Today it will not launch anymore. 
I had not done any update for some time so updates are probably not the cause of this. 
Also this failed launch does not seem to produce any error in the logs.

[Update: just saw your post avs1988 about the global service crash; thanks for this; I was starting worrying about the stability of my Ubuntu installation!!]

---

### Post by Kivech on 2011-05-26
SIMPLE FIX:

Go to your home folder
```
cd ~/
```

Turn on hidden files and folders

Navigate to the folder ./Skype

Open it and delete the file shared.xml

You will have to reconfigure skype, but you will be able to use the service again.

---

### Post by eMKi on 2011-05-27
> **Kivech said:**
> SIMPLE FIX:

Go to your home folder
```
cd ~/
```Turn on hidden files and folders

Navigate to the folder ./Skype

Open it and delete the file shared.xml

You will have to reconfigure skype, but you will be able to use the service again.


This worked for me!
Kivech thank you!

---

### Post by Ashin Sopaka on 2011-05-29
pardon the ignorance, what needs to be reconfigured in skype? the shared.xml file keeps being recreated during the log-in process.

thanks

---

