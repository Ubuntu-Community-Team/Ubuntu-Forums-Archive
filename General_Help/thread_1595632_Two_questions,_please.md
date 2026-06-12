---
title: "Two questions, please?"
date: 2010-10-13
forum: General Help
---

### Post by ssmiley12 on 2010-10-13
I am fairly new to Ubuntu, now have version 10.10 installed.  I have a couple questions, probably simple (or maybe even dumb). 

First dumb question :  I am of the opinion that KDE programs will not run if using Gnome, is that correct? I wanted to install a financial application, but it is for KDE.  If my assumption is true (KDE / Gnome) then I will find another application.

Second dumb question:  After a time of inactivity, the computer goes to sleep or inactive, and then I get a screen wanting me to enter a password to use the system again.  I do not need this feature at all, but so far, have not found where to change it.

Thanks in advance for any help.

S.

---

### Post by lukeiamyourfather on 2010-10-13
A boss of mine once said there are no dumb questions, but you might get a dumb answer. :)

> **ssmiley12 said:**
> 
First dumb question :  I am of the opinion that KDE programs will not run if using Gnome, is that correct? I wanted to install a financial application, but it is for KDE.  If my assumption is true (KDE / Gnome) then I will find another application.


Applications for either KDE or GNOME can be run in either environment. When installing an application it will install required packages as needed whether those packages are part of KDE or GNOME.

> **ssmiley12 said:**
> 
Second dumb question:  After a time of inactivity, the computer goes to sleep or inactive, and then I get a screen wanting me to enter a password to use the system again.  I do not need this feature at all, but so far, have not found where to change it.


I don't have Ubuntu in front of me to find it, but there's a way to change this. I'll let someone else answer this one.

---

### Post by emoguitarist06 on 2010-10-13
System > Preferences > Screensaver
Uncheck the box where it says to activate screensaver when idle
or if you want the blank screen but w/o the password
there should be a box for that too

---

### Post by cpmman on 2010-10-13
System - Preferences - Screensaver - Power Management

---

### Post by ean5533 on 2010-10-13
> **lukeiamyourfather said:**
> Applications for either KDE or GNOME can be run in either environment. When installing an application it will install required packages as needed whether those packages are part of KDE or GNOME.

This guy is correct. The only issue you'll see is that applications designed for KDE may not blend as nicely into a GNOME desktop (and vice versa). The program will still be fully functional, but it just might not have the same "look and feel" that a GNOME application will have.

---

### Post by WorMzy on 2010-10-13
You can run KDE apps on GNOME desktop, but the KDE desktop will have to be installed too, which uses a lot of disk space. For a single application I'd say that it's not really worth it, but that's just my opinion.

---

### Post by emoguitarist06 on 2010-10-13
> **WorMzy said:**
> You can run KDE apps on GNOME desktop, but the KDE desktop will have to be installed too, which uses a lot of disk space. For a single application I'd say that it's not really worth it, but that's just my opinion.

I don't believe this is true.

I run only two KDE apps "KRenamer" & "K3b" (I think those are the names)

But installing KDE is a little extreme and not needed from my experience

---

### Post by emoguitarist06 on 2010-10-13
> **lukeiamyourfather said:**
> 
Applications for either KDE or GNOME can be run in either environment. When installing an application it will install required packages as needed whether those packages are part of KDE or GNOME.

Agreed

---

### Post by ean5533 on 2010-10-13
> **emoguitarist06 said:**
> I don't believe this is true.

I run only two KDE apps "KRenamer" & "K3b" (I think those are the names)

But installing KDE is a little extreme and not needed from my experience

Well, it depends on what libraries those applications depend on. If <random KDE app> depends on kde-core, then it's going to install basically everything that is in KDE.

---

### Post by ssmiley12 on 2010-10-13
I sincerely want to thank all of you for your quick response and for your help and information.  Pretty new tio Ubuntu but love it.  Thanks again.

S.

---

### Post by ssmiley12 on 2010-10-13
I hope the quick reply I sent is viewable to / by all who responded???? Thanks again.

---

### Post by ssmiley12 on 2010-10-13
Emo,

I have a friend, Shawn Pittman who is from Texas, I know, it is a big state,  He has a rythhm and blues group, plays some ploace or places in Austin.  Has a number of CDs or DVDs out.  Ever heard of them?

Thanks again

S.

---

### Post by emoguitarist06 on 2010-10-13
> **ssmiley12 said:**
> Emo,

I have a friend, Shawn Pittman who is from Texas, I know, it is a big state,  He has a rythhm and blues group, plays some ploace or places in Austin.  Has a number of CDs or DVDs out.  Ever heard of them?

Thanks again

S.

I'm actually new to the Austin area but I absolutely love it!
I'll look him up. Do you know where they play at usually?

---

### Post by WorMzy on 2010-10-13
> **emoguitarist06 said:**
> I don't believe this is true.

I run only two KDE apps "KRenamer" & "K3b" (I think those are the names)

But installing KDE is a little extreme and not needed from my experience

You're kinda right, krename needs to install 87MB worth of dependencies on my GNOME-only desktop, but doesn't need to install KDE itself, just the kdelibs. However, k3b needs 150MB worth of dependencies, including kdebase-runtime.

I guess it depends on each application. Still, 87MB is a lot of "extra" stuff for a simple batch file renamer. Especially when there's gprename for GNOME which takes up a whopping 0.34MB. :P

Same goes for k3b, when there's brasero and/or recorder for GNOME.

---

### Post by dani12817 on 2010-10-15
.

---

### Post by dani12817 on 2010-10-15
> **ssmiley12 said:**
> 
First dumb question :  I am of the opinion that KDE programs will not run if using Gnome, is that correct? I wanted to install a financial application, but it is for KDE.  If my assumption is true (KDE / Gnome) then I will find another application.

First question- All ubuntu programs are compatible with all desktops, both KDE and GNOME
> **ssmiley12 said:**
> 
Second dumb question:  After a time of inactivity, the computer goes to sleep or inactive, and then I get a screen wanting me to enter a password to use the system again.  I do not need this feature at all, but so far, have not found where to change it.

Second questions- System> Preferences> Screensaver
And uncheck "Lock screen when screensaver is active"

---

