---
title: "Compiz"
date: 2012-07-04
forum: General Help
---

### Post by Penfold1971 on 2012-07-04
I have a window alerting me that :

"The application Compiz has closed unexpectedly"

I'm a newcomer to Ubuntu as of 25th June, so am very gingerly finding my way around. What should I do about this alert?

The details show (among many other things)
ProblemType
    Crash
Title
    compiz crashed with SIGSEGV in CompositeScreen::compositingActive()

---

### Post by msammels on 2012-07-04
If it's just a single crash, don't worry about it. If it continually happens, let us know. It's a graphics issue.

---

### Post by matt_symes on 2012-07-04
Hi

Welcome to the forums Penfold1971 :D

> **Penfold1971 said:**
> I have a window alerting me that :

"The application Compiz has closed unexpectedly"

I'm a newcomer to Ubuntu as of 25th June, so am very gingerly finding my way around. What should I do about this alert?

The details show (among many other things)
ProblemType
    Crash
Title
    compiz crashed with SIGSEGV in CompositeScreen::compositingActive()

My first question would be, is the crash causing you any noticable problems while running Ubuntu ?

Kind regards

---

### Post by raja.genupula on 2012-07-04
Its actually a Bug , see here [http://www.google.com/search?q=compiz+crashed+with+SIGSEGV+in+CompositeScreen%3A%3AcompositingActive%28%29&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=compiz+crashed+with+SIGSEGV+in+CompositeScreen%3A%3AcompositingActive%28%29&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)

---

### Post by Penfold1971 on 2012-07-04
It's happened more than once. I just clicked on the relaunch button, but the last time wondered if it was a serious issue requiring some drastic action on my part (like a re-install).

---

### Post by Penfold1971 on 2012-07-04
> **matt_symes said:**
> My first question would be, is the crash causing you any noticable problems while running Ubuntu ?

Not that I'm aware of, but my level of awareness is not high, being very new to Ubuntu.

I'm only using this machine for one thing, running Folding@home. So far all of the flow and return work units has been without hitch.

I should perhaps say that the version of Ubuntu is 12.04

---

### Post by matt_symes on 2012-07-04
Hi

If it's not causing you a problem and you only use that machine for one purpose then it may be best to leave it and just update Ubuntu frequently.

EDIT: Out of interest, what version of Ubuntu are you using ?

Kind regards

---

### Post by Penfold1971 on 2012-07-04
> **matt_symes said:**
> Hi

If it's not causing you a problem and you only use that machine for one purpose then it may be best to leave it and just update Ubuntu frequently.

EDIT: Out of interest, what version of Ubuntu are you using ?

Kind regards

I'm using 12.04

Having been a Mac user for the past twenty years, it's interesting to see another OS up close.
I'm keen to learn as much as I can, bit by bit, about it. When an alert like the one I described pops up, it could mean anything when you're new to the scene.

---

### Post by matt_symes on 2012-07-04
Hi

If you wanted to be proactive you could raise a bug report for it on Launchpad.

That would be a good way to get involved in the community.

Compiz crashed and quite dramatically (seg fault) but it restarted correctly.

You may want to look in the logs. Ubuntu (and Linux in general) is far more verbose when thing crash so bug reports can be raised.

Windows and mac less verbose (for obvious reasons), but their sofware does still crash.

Kind regards

---

### Post by Petro Dawg on 2012-07-04
If using Ubuntu12.04, be sure to run the following commands in terminal to fix all the little bugs with cube rotation and workspace switching.

sudo add-apt-repository ppa:vanvugt/compiz-preproposed
 sudo apt-get update
sudo apt-get upgrade

... also a restart is usually required

It took me forever to find this bug fix the first time.

---

### Post by Penfold1971 on 2012-07-04
> **Petro Dawg said:**
> If using Ubuntu12.04, be sure to run the following commands in terminal to fix all the little bugs with cube rotation and workspace switching.

sudo add-apt-repository ppa:vanvugt/compiz-preproposed
 sudo apt-get update
sudo apt-get upgrade

... also a restart is usually required

It took me forever to find this bug fix the first time.

Now this is where I need some close guidance, please. I'm not well versed in these matters.

Do I run each command one at a time and, in the case of the last two, wait until I get some notification that the update/upgrade has occurred? And only then do a Restart? Or is a Restart required after each command has run?

Please excuse my ignorance and caution.

---

### Post by Penfold1971 on 2012-07-04
> **matt_symes said:**
> Hi

If you wanted to be proactive you could raise a bug report for it on Launchpad.

That would be a good way to get involved in the community.

Compiz crashed and quite dramatically (seg fault) but it restarted correctly.

You may want to look in the logs. Ubuntu (and Linux in general) is far more verbose when thing crash so bug reports can be raised.

Where would I find the logs? And, is it obvious how to go about raising a bug report?

---

### Post by matt_symes on 2012-07-04
Hi

> Where would I find the logs? After thinking about it, I think the logs may not be appropiate here.

> And, is it obvious how to go about raising a bug report?You would want to create an account on Launchpad and raise the bug.

The general steps are outlined here.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

To raise the bug, after it has crashed, open a terminal and type

```
ubuntu-bug compiz
```> Now this is where I need some close guidance, please. I'm not well versed in these matters.

Do I run each command one at a time and, in the case of the last two,  wait until I get some notification that the update/upgrade has occurred?  And only then do a Restart? Or is a Restart required after each command  has run?

Please excuse my ignorance and caution.This is not a PPA i have ever used so i cannot say whether it is applicable to your problem even though it solved Petro Dawg's problem. I'll leave it up to you whether to install it or not.

I will detail how to run the commands though...

To run the commands, open a terminal and type each command one after an other.

The first command will require you to enter your password. It will not be echoed to the screen.

The other commands will not require you to enter your password as long as they are typed in before the sudo timer times out (default 15 minutes IIRC).

There is no need to reboot after each command, only after the last command (If you were to restart lightdm from the console there should be no need to reboot at all but a reboot is easiest). 

You will see when they have finished running.

Kind regards

---

### Post by Petro Dawg on 2012-07-04
Matt_symes is correct, the bug fix I mentioned may not fix your specific problem.  But it does fix many common problems you may not have noticed yet such as screen flicker during cube rotation and the inability to move open windows to new cube faces using keyboard short cuts.

I merely do not want you to be left with more little annoyances to overcome.

And I would also add, it doesn't sound as if you actually have an issue.  I've also had those "crash" messages appear when messing with Compiz, it seems to be a fickle program.  I don't believe anything serious is going on.

---

### Post by Penfold1971 on 2012-07-04
Thanks for all that, matt. I've archived your post so I can consult it as and when the alert occurs again. I'll read up on Launchpad and bugs listed. It's quite long, I notice, and at first read I didn't see exactly the one with the same title as mine.

---

### Post by Penfold1971 on 2012-07-04
> **Petro Dawg said:**
>  ... it does fix many common problems you may not have noticed yet such as screen flicker during cube rotation and the inability to move open windows to new cube faces using keyboard short cuts.
I don't actually do much on my Ubu machine except check in to see how the latest 'Folding@home' work unit is getting on, what it's about etc. That said, I can't remember exactly what I *was* doing when the alert came up. (I'm not sure what 'cube rotation' is, to be honest. :) )

> **Petro Dawg said:**
> I merely do not want you to be left with more little annoyances to overcome.
Understood, and thanks!

> **Petro Dawg said:**
> And I would also add, it doesn't sound as if you actually have an issue.  I've also had those "crash" messages appear when messing with Compiz, it seems to be a fickle program.  I don't believe anything serious is going on.
Well, it certainly hasn't affected my Folding@home activities, thankfully. But you know how it is with something new ... the slightest hiccup and you fear the worst.

---

### Post by Penfold1971 on 2012-07-04
I should mark this thread as 'Solved' for now, I think.

Thanks for all of your replies.

---

### Post by prshah on 2012-07-05
> **Penfold1971 said:**
> I should mark this thread as 'Solved' for now, I think.

Penfold, please update your system with the latest updates.

You are not alone in this, see: [http://ubuntuforums.org/showthread.php?t=1971928](http://ubuntuforums.org/showthread.php?t=1971928)

I too was facing this error initially, but it seems to have gone away slowly with updates. Still get it sometimes, occasionally though (maybe about 1-2 times a month only, now)

I don't suggest a re-install yet.

---

### Post by Penfold1971 on 2012-07-05
> **prshah said:**
> Penfold, please update your system with the latest updates.

You are not alone in this, see: [http://ubuntuforums.org/showthread.php?t=1971928](http://ubuntuforums.org/showthread.php?t=1971928)

I too was facing this error initially, but it seems to have gone away slowly with updates. Still get it sometimes, occasionally though (maybe about 1-2 times a month only, now)

I don't suggest a re-install yet.

Thanks for the info about this error. I have been installing updates - the latest single one today.

Is there an automatic prompt to download and install them? I've been looking in 'Software Updater' in the menu at the top right of the screen, so doing things manually.

I am re-assured that I don't need a re-install. I can't imagine what might have happened to require one, but you never know I suppose. It's not as if I've been recklessly downloading all sorts of dodgy stuff - only the mandated updates.

---

### Post by prshah on 2012-07-05
> **Penfold1971 said:**
> Is there an automatic prompt to download and install them? 

Yes, but it runs only once a day by default. 

Software center is a little too slow for my liking. If you would like to speed up updates:

1) The GUI way: Press Alt+F2 (Or open Dash) and give the command```
gksudo update-manager
```

2) The terminal (Dash-Terminal) way:```
sudo apt-get update && sudo apt-get -y upgrade
``` (-y = don't prompt)

---

