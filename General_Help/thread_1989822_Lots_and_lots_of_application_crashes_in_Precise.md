---
title: "Lots and lots of application crashes in Precise"
date: 2012-05-28
forum: General Help
---

### Post by DarkShades on 2012-05-28
I've upgraded 3 of my 4 computers to Precise.  The trouble is the same applications on each keep crashing setting off Apport showing me the details about what happened.

I use a default install of Xubuntu for the XFCE desktop, then install KDE for systems that can handle it.

At first I thought about RAM since two of them are running about bit light on RAM but my main workstation has 4GB and it gets the same errors.  Plus my entertainment system and my laptop are 32 bit P4 based technologies .  My workstation is an AMD Athlon II X2.

The big crashy apps mostly have been XBMC, MyPaint, plus some others that randomly crash at times.  Sometimes they will be more system specific programs.

I use XBMC and Miro a lot so it's not really a surprise they have been the most noticed error generators.

I can't think of what might be making these systems act like this when up to 11.10 all was well.

I did a fresh install on the entertainment and mobile systems, I did an upgrade from install USB stick for  the workstation so even there I can't seem to find a common root problem.

Anyone have any ideas where the crashiness is originating from?

---

### Post by Baneblade on 2012-08-16
I'm getting similar crashes on Xubuntu 12.04. They don't appear to be limited to specific applications. I can't reliably reproduce crashes, I'm just getting lots and lots, seemingly at random.

I don't have a solution for you, I just wanted to add a "me too" so you know it isn't just you.

EDIT: System in question is not the one in my sig.
HP 2710us (Core2-Duo, 4GB RAM, 7200RPM HDD) Default partition scheme and full disk encryption.

---

### Post by Baneblade on 2012-08-23
I have been able to reproduce crashes in XFCE4-power-manager simply by plugging in or removing the AC charger.

---

### Post by Bucky Ball on 2012-08-23
Do you mean you then install KDE or Kubuntu-desktop? If so, you would be much better off installing Kubuntu, then install xfce4 DE from Software Centre or Synaptics. That will install ONLY the desktop environment for Xubuntu, not all apps and other packages. 

The problem may be a conflict between apps in Xubuntu and Kubuntu. I'm just wondering why you are installing a light OS then dropping the heaviest DE on it? You are partial to the KDE DE?

Suggestion: Run your apps from a terminal to get more clues. You will need to find the commands to launch them. You can simply try 'xbmc' or 
'miro' in a terminal for starters. That should launch them and when they crash, check the terminal and post the error back here. ;)

---

### Post by Baneblade on 2012-08-23
I don't have any KDE dependant apps or the KDE DE installed.

The OP and I are seeing lots of crashes on plain Xubuntu systems as well.

---

### Post by Bucky Ball on 2012-08-23
> **Baneblade said:**
> I don't have any KDE dependant apps or the KDE DE installed.

The OP and I are seeing lots of crashes on plain Xubuntu systems as well.

Perhaps not, but I am addressing the original poster. This is a good example of why hijacking is discouraged; it gets confusing. As your issue is NOT the same (OP *does* have KDE installed) please post a new thread with a descriptive title outlining your specific problems and keep an eye on this one (adding anything you can, naturally). 

OP said nothing about seeing crashes on plain Xubuntu install. ;)

---

### Post by Baneblade on 2012-08-23
Ok will do! Thanks :)

---

### Post by Merrattic on 2012-08-27
> OP said nothing about seeing crashes on plain Xubuntu install.

But this is a common problem with Xubuntu Precise judging by the number of posts already on this subject on the forum, so it is worth not discounting the fact that other have the problem, even without KDE. I would point the finger at the core 12.04 Xubuntu having seen this behaviour across 4 different installations. I can get a crash report on demand every time I print something :)

Would be interested to know what happens if you uninstall Apport?

---

### Post by Baneblade on 2012-08-27
> **Merrattic said:**
> 
Would be interested to know what happens if you uninstall Apport?

I've just disabled Apport service and stopped it from starting at boot, with a bit of help from google.

I can no longer reproduce the power-manager I crash mentioned earlier!

It's too early to say if this is the cause of the other "crashiness" yet, but it's looking good so far!

Thanks!

---

### Post by Merrattic on 2012-08-27
To disable apport you need to edit 

/etc/default/apport

```
sudo nano /etc/default/apport
```Change enabled from "1" to a "0" so it looks like this:
  
enabled=0

To turn it on make it:
  
enabled=1

:)

---

### Post by Baneblade on 2012-08-27
Yes, correct.

Sorry I should have put that in for others reading this for the fix.

Thanks ;)

---

### Post by Bucky Ball on 2012-08-27
> **Merrattic said:**
> But this is a common problem with Xubuntu Precise judging by the number of posts already on this subject on the forum, so it is worth not discounting the fact that other have the problem, even without KDE.

Correct. We shouldn't discount them. But this thread is not about them, it is about the OP and their specific issue. ;)

---

### Post by Merrattic on 2012-08-28
Waits to hear back from OP................................................................;)

---

