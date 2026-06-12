---
title: "Ubuntu crashes, and crashes, and crashes"
date: 2011-03-13
forum: General Help
---

### Post by raincity on 2011-03-13
In the last month I installed Ubuntu 10.10 twice on a stock Thinkpad T43.  I am writing this on that same laptop using Windows XP because I am unable to use Ubuntu for any length of time without it freezing up completely.  When that happens there are no logs files produced, all hard drive access stops and none of the key combinations posted in various Ubuntu help pages do anything.  The reason it was installed twice was to try to resolve this problem.  Windows XP is very slow and has other issues you all are probably well aware of, but complete crashes are extremely rare, in fact I don't remember the last time XP did crash on this machine.

I've installed various Ubuntu versions on various hardware platforms maybe 15 times over the past few years and have never been able to achieve a stable environment.  Although I've really enjoyed using Ubuntu when it has worked I'm at a loss to how to resolve this problem and at this point wonder how those of you that use Ubuntu daily have been able to to so.  My installations are plain vanilla configurations, I'm doing nothing remotely exotic and the lockups start almost immediately after installation before I load any additional packages.  It seems I am always moving the mouse when they do occur.

Am I running a version that isn't stable?  Should I go back to an older version?  Or are these kinds of problems to be expected in many Ubuntu installations?

---

### Post by uRock on 2011-03-13
What have you tried as far as troubleshooting is concerned?

Did you test the ISO image that you downloaded?

Did you test the LiveCD before using it to install?

What hardware are you having these problems on?

More information is needed to figure out what is causing your problems. I have only had a hand full of crashes in the two years I have been using Ubuntu and most of those were cause by me breaking the system.

---

### Post by HermanAB on 2011-03-13
Howdy,

Version 10.10 is probably the most unstable Ubuntu ever.  Most trouble seems to be due to the video drivers.  So you could try changing to the VESA driver and see whether the problems go away.

Otherwise, if you are not comfortable debugging things yet, switch to a different distribution such as Fedora, PCLinuxOS or OpenSuse.

---

### Post by raincity on 2011-03-13
What have you tried as far as troubleshooting is concerned?

[COLOR="Blue"]I've searched extensively for others having this problem, hoping someone else has resolved it.  Others do have the problem, but I've yet to come across a solution.  I'm not sure how to approach it besides that.  I'm expert at dealing with Windows problems (I kind of have to be) but still only moderately familiar with Ubuntu.[/COLOR]

Did you test the ISO image that you downloaded?

[COLOR="Blue"]Yes[/COLOR]

Did you test the LiveCD before using it to install?

[COLOR="Blue"]I used it for maybe 2 hours and it worked fine.  Sometimes I can get 2 hours or so out of my hard drive installation before it locks up so I don't think that means much.[/COLOR]

What hardware are you having these problems on?

[COLOR="Blue"]A stock Thinkpad T43 with ATI graphics.[/COLOR]

More information is needed to figure out what is causing your problems. I have only had a hand full of crashes in the two years I have been using Ubuntu and most of those were cause by me breaking the system.

[COLOR="Blue"]I want YOUR installation.[/COLOR]

---

### Post by raincity on 2011-03-13
> **HermanAB said:**
> Howdy,

Version 10.10 is probably the most unstable Ubuntu ever.  Most trouble seems to be due to the video drivers.  So you could try changing to the VESA driver and see whether the problems go away.

Otherwise, if you are not comfortable debugging things yet, switch to a different distribution such as Fedora, PCLinuxOS or OpenSuse.

Is there an easy way to change to the VESA driver without editing the X11.org file?  I've completely trashed my previous Linux installations a few times doing that.

---

### Post by uRock on 2011-03-13
Can you give us some specific problems/errors to help with troubleshooting?

---

### Post by raincity on 2011-03-14
> **uRock said:**
> Can you give us some specific problems/errors to help with troubleshooting?

There are no errors.  The system locks up completely.  Hard drive access stops, it doesn't respond to any key presses and no logs are generated.  It must be powered down once this happens.

I'd love some errors or a log file.  At least I'd have a place to start.

---

### Post by p110011 on 2011-03-15
> **raincity said:**
> There are no errors.  The system locks up completely.  Hard drive access stops, it doesn't respond to any key presses and no logs are generated.  It must be powered down once this happens.

I'd love some errors or a log file.  At least I'd have a place to start.

I'm getting the same hard lock. I have to hard shut-down.

HPZV5000 laptop
2.6.32-30-generic 10.04 Lucid
P4 3.2 Ghz
2 GB
ATI mobility

---

### Post by p110011 on 2011-03-26
Been a fews days now, after I got an updated kernal (-31-generic) and I have not seen any hard locks.

Xing fingers.

---

### Post by camaross on 2011-03-27
Same here. Ubuntu 10.10 crashes on me constantly. I need to use Linux for my work. This is super frustrating. :(

Lenovo laptop
Intel Core i5
4 GB

> **p110011 said:**
> I'm getting the same hard lock. I have to hard shut-down.

HPZV5000 laptop
2.6.32-30-generic 10.04 Lucid
P4 3.2 Ghz
2 GB
ATI mobility

---

### Post by coldraven on 2011-03-27
I've been using 10.10 64bit since it was released, the only problem I had was with 64bit Flash crashing Firefox. Since updating to Firefox 4 I've not had a crash.
HP Compaq 6715b, 2xAMD Turion, 4GB, ATI X1250

---

### Post by gordintoronto on 2011-03-27
How hot is your computer? IBM/Lenovo laptops have a reputation for overheating in Ubuntu. 

Right-click on the top panel, select "Add to panel," and "Hardware Sensors Monitor." The applet doesn't do anything until you right-click on it and select "preferences" to configure it. For details, see Issue 43 of Full Circle Magazine, page 34.

My computer has not crashed in five months. Your experience is extremely unusual.

---

### Post by Alan.Brown on 2011-03-28
This is the same problem as in this thread - [http://ubuntuforums.org/showthread.php?t=1714387&highlight=freezing](http://ubuntuforums.org/showthread.php?t=1714387&highlight=freezing)

This my post to that thread -

> 
I am using a brand new  HP-200-5220a computer and have been having freezing in both Ubuntu 10:10 AND Linux Mint 10 AND openSuSE 10.3 for a couple of months!!   The freezing does NOT occur under Windows 7 on the same machine.  All the above are installed on the hard disk - not run from live DVDs.

I have run memtest several times without any errors.   None of the system logs show any error (understandable because the freezing may block any error message from being logged).   CPU temperature is usually between 30 and 33 C.

I have tried several forums and noticed that this is a very common  problem on many different makes and models of computer.   This would  suggest that the problem is not hardware related.

Since three distros have been involved I assume that it is a bug in  Linux and that (maybe!!) it will disappear in time hopefully with the  next version.

When the system freezes there is only one thing that will work - Alt+SysRq+B - **in that order** - this will reboot the computer.

I have not been able to get any help on this matter over the past two months.

Any more suggestions??   Any help??


Similar threads - 
[http://ubuntuforums.org/showthread.php?t=1712505&highlight=freezing](http://ubuntuforums.org/showthread.php?t=1712505&highlight=freezing).   
[http://ubuntuforums.org/showthread.php?t=1478787&highlight=freezing](http://ubuntuforums.org/showthread.php?t=1478787&highlight=freezing)
[http://ubuntuforums.org/showthread.php?t=1703000&highlight=freezing](http://ubuntuforums.org/showthread.php?t=1703000&highlight=freezing)
[http://ubuntuforums.org/showthread.php?t=1686265&highlight=freezing](http://ubuntuforums.org/showthread.php?t=1686265&highlight=freezing)
... and so on!!

@ gordintoronto - judging from the number of entries in these threads (and others) it seems to be a very common problem and no-one seems to know the solution.  My computer runs at between 30 and 33 C.

Alan

---

### Post by gordintoronto on 2011-03-28
> **Alan.Brown said:**
> @ gordintoronto - judging from the number of entries in these threads (and others) it seems to be a very common problem and no-one seems to know the solution.  My computer runs at between 30 and 33 C.

Alan

I wish people would write enough detail about their computers, and the crashes, that someone could figure out what they have in common.

"Very common" is relative. Thousands of people have not written about having a problem, dozens (?) say they do have the problem.

What part of your computer runs at 30 to 33C? On my desktop, I monitor the temperatures of one CPU, the chipset, the hard drive and the video card. The hard drive typically is at 31 to 33, but the video card is often at 49. The CPU has the widest range, depending on what I'm doing.

---

### Post by Alan.Brown on 2011-03-28
@gordintoronto

You are right - "very common" is relative.   I did not intend to suggest that thousands were having a freezing problem.   Rather I wanted to suggest that the problem was not isolated to one make of computer, one make of Video card or even one particular distribution of Linux.

To me this would suggest that the problem is software related rather than hardware related and probably within Linux itself.   By referring to posts of other peoples' problems I hoped to refer to a wide range of details from several posters so that this problem may be isolated.

FWIW the specs of my computer are at - 
[http://www.techbuy.com.au/p/157794/SYSTEMS_HP_COMPUTERS/HP/BU089AA.asp](http://www.techbuy.com.au/p/157794/SYSTEMS_HP_COMPUTERS/HP/BU089AA.asp)

The temperature I quoted is that of the CPU.   I have given as much detail as I thought relevant but would be willing to supply more information if you would suggest what would help.  It would be nice if we could all work together to solve this.

Alan

---

### Post by raincity on 2011-03-29
> **gordintoronto said:**
> How hot is your computer? IBM/Lenovo laptops have a reputation for overheating in Ubuntu. 

Right-click on the top panel, select "Add to panel," and "Hardware Sensors Monitor." The applet doesn't do anything until you right-click on it and select "preferences" to configure it. For details, see Issue 43 of Full Circle Magazine, page 34.

My computer has not crashed in five months. Your experience is extremely unusual.

Checked it out.  No heat problems here.  Thanks for the suggestion.

---

### Post by gordintoronto on 2011-03-29
> **Alan.Brown said:**
> FWIW the specs of my computer are at - 
[http://www.techbuy.com.au/p/157794/SYSTEMS_HP_COMPUTERS/HP/BU089AA.asp](http://www.techbuy.com.au/p/157794/SYSTEMS_HP_COMPUTERS/HP/BU089AA.asp)



I'm fascinated. This is recent, but not exactly state of the art technology, so I would expect Linux to support it very well.

Have you ever tried another distro?

---

### Post by Alan.Brown on 2011-03-30
The computer is off the market now - I was lucky to get a run-out version - $1133 reduced to $899 (Australian Dollars, ie REAL dollars :P).

I am running Ubuntu 10.10, openSuSE 11.3 and Linux Mint 10 - all with the same freezing problem.   Originally I thought the problem was in Firefox but it has occurred in other applications, in Nuatilus and others.   Everything runs very well "out of the box" - the only problem is freezing about once or twice a day (say, 10 hours work) over the last two months.

Windows 7 is on the same computer and I have had no freezing problems with it.  I don't use in very often and I always wash my hands afterwards!!  :D

I am also running Ubuntu and Linux Mint (same versions as above) on an older computer - circa 2006 - and have never had any problems.   Could the current problem be with drivers for more recent hardware - like NVIDIA or WiFi??

Alan

---

### Post by gordintoronto on 2011-03-31
> **Alan.Brown said:**
> I am also running Ubuntu and Linux Mint (same versions as above) on an older computer - circa 2006 - and have never had any problems.   Could the current problem be with drivers for more recent hardware - like NVIDIA or WiFi??

Alan

I really don't know. I have an AMD-based system which would sometimes freeze in 10.04 when it was cold, but it has been rock solid in 10.10 -- until the video card blew up. :(

(Note that 10.04's kernel did not fully support the latest AMD processors, but 10.10 does. Specifically, it can read the temperature sensors.)

---

