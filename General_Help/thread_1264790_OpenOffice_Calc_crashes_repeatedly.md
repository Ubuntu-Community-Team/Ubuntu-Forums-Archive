---
title: "OpenOffice Calc crashes repeatedly"
date: 2009-09-12
forum: General Help
---

### Post by Mander on 2009-09-12
I haven't been able to pinpoint just what the problem is, but OpenOffice Calc seems to crash constantly.  Generally it seems to happen after I insert or delete columns, rows, or cells via right-click.  But it doesn't happen every time.

I've seen so many similar problems on google, etc. but I haven't been able to find one that is specifically relevant.  Has anyone had any luck in fixing this?  Or locating the specific bug report?

---

### Post by Hagar Delest on 2009-09-12
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Mander on 2009-09-13
Hi, I've done both of those things, and now (with the "vanilla" OpenOffice installed) things are even worse.  I can't open the Extension Manager, and the document recovery fails.

Any ideas?

---

### Post by fanglinyong on 2009-09-13
what's your ooo's version?

---

### Post by Mander on 2009-09-13
3.1.1, English version, for 64bit systems.

Downloaded from here:

[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxx86-64wjre&lang=en-US&version=3.1.1](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxx86-64wjre&lang=en-US&version=3.1.1)

---

### Post by Mander on 2009-09-13
Well, I needed to get some work done so I installed 2.4 (couldn't find a 64 bit version so I installed the 32 bit with the force architecture command).  Calc seems to be working for the moment.

However, Base complains about not having a Java Runtime Environment now.  I can't seem to get it to recognize the ones that are installed.

Do you suppose I could enable the Hardy repository, install OpenOffice from there, and then lock the version?  That's how I downgraded Kile.

---

### Post by Mander on 2009-09-15
> **Mander said:**
> 
Do you suppose I could enable the Hardy repository, install OpenOffice from there, and then lock the version?  That's how I downgraded Kile.

Actually, that didn't work, either.  I eventually got frustrated and after a long process got rid of everything new and re-installed the version from the repository.

So, I am back to the original problems. To be more specific:

-Calc intermittently, but frequently, crashes when deleting rows/columns/cells.

-Opening the data pilot is a real exercise in frustration. It takes at least a minute to respond, during which time the CPU useage sometimes jumps up to 86% or more.  The entire system becomes incredibly slow, so that even trying to move the mouse across the screen is impossible. The hard drive grinds away during this time.

-Sometimes trying to open the data pilot locks up the entire system and I have to restart it.

Can anyone point me to the appropriate bug report for this, or to instructions on how to figure out what is going wrong?

The version I have installed right now is 1:3.0.1-9ubuntu3.  It's whatever is in the Jaunty repository.

**_ETA_**:

I attempted to generate a backtrace using the instructions [here]("http://wiki.services.openoffice.org/wiki/Providing_a_gdb_backtrace").  For whatever reason, doing that made the whole system lock up so badly that even after leaving it running for half an hour, it was still frozen but the hard drive was churning away madly. I could get to a console window (ctl+alt+f1) but half an hour after entering my user name it still hadn't come back to ask me for my password so that I could see what was running. I ended up having to force the computer to shut down with the power button.

---

### Post by chudder on 2009-09-30
I've been having a general problem with OO crashing, not often but when it does, it's very inconvenient timing.  Sometimes when I click on the File menu, it says something to the effect of, "OpenOffice doesn't have a Java Runtime Environment, and will shut down immediately."  

Also it won't install extensions, saying it needs "A Java Reimplementation" or something like that.

I've installed most JRE apps from synaptic I can find.

It's not a big problem, just really annoying sometimes.

---

### Post by Hagar Delest on 2009-10-01
Do you have a JRE version _checked_ in Tools>Options>OOo>Java?

---

### Post by chudder on 2009-10-01
actually, I reinstalled the java-common file and then I selected one in OO.  Thanks though.

---

### Post by Radonballoon on 2009-10-15
I've been having this exact same problem for about a week now. Randomly it seems, calc will cause a system freeze, so I have to do a manual reboot. I'll be resizing things, dragging cells, copying, saving, just about anything you can do in calc causes a freeze. It seems that the larger or more complicated the spreadsheet the more frequent the freezes. It's incredibly aggravating. Any info would be great

---

### Post by Mander on 2009-10-27
I just quit struggling with it in the end, and I'm using portable OOo under Wine to do any serious spreadsheet work.  Ridiculous, I know, but it works.

Other aspects of OOo are fine (database, writer, etc.).

---

### Post by chudder on 2009-10-27
Mander,

I reinstalled the jre OO package in synaptic and selected in OO and it works now.  I don't know if that's even relevant to your problem or not.

---

