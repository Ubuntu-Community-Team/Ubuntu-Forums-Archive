---
title: "Memory leaking process causing hang after login"
date: 2011-06-10
forum: General Help
---

### Post by overtone on 2011-06-10
Hello everyone,

Im still pretty new to the linux scene but kubuntu has been a great alternative to ubuntu (unity, ugh) until now.

It only started happening since i started messing around with play on linux but i dont think their related. I dont think its a driver issue either as ive switched between proprietary and default to no avail.

Basically after i log in, it takes over 3-6 minutes getting slower and slower before finally getting back to regular speed. So after a few occurences i decided that immediately after startup i went to system monitor and sure enough;

There is a process title "akonadi_contact" that is slowly growing in memory. There are also multiple occurences of it (usually between 6 and 9). they keep growing usually to the 500000k mark in memory usage before turning gray (swap storage??) and then eventualy the end.

What is "akonadi_contact"
How do i stop this from happening.
Is this a memory leak?

i already rolled back what i did with play on linux.

Lastly I just noticed there are other processes with akonadi as their prefix. they do grow quite alarmingly in size but they seem to die first.

They are

akonadi_Ical_re
akonadi_nepomuk
akonadi_maildir

---

### Post by iclestu on 2011-06-10
> **overtone said:**
> Hello everyone,

Im still pretty new to the linux scene but kubuntu has been a great alternative to ubuntu (unity, ugh) until now.

It only started happening since i started messing around with play on linux but i dont think their related. I dont think its a driver issue either as ive switched between proprietary and default to no avail.

Basically after i log in, it takes over 3-6 minutes getting slower and slower before finally getting back to regular speed. So after a few occurences i decided that immediately after startup i went to system monitor and sure enough;

There is a process title "akonadi_contact" that is slowly growing in memory. There are also multiple occurences of it (usually between 6 and 9). they keep growing usually to the 500000k mark in memory usage before turning gray (swap storage??) and then eventualy the end.

What is "akonadi_contact"
How do i stop this from happening.
Is this a memory leak?

i already rolled back what i did with play on linux.

Lastly I just noticed there are other processes with akonadi as their prefix. they do grow quite alarmingly in size but they seem to die first.

They are

akonadi_Ical_re
akonadi_nepomuk
akonadi_maildir

akonadi, as i understand it, is the data storage and retrieval system that sits behind a lot of kde's features...

As to why it may be causing the problems you describe, I cannot help im afraid. I do get a fair number of akonadi processes without any noticable difficulties or memory leak

---

### Post by overtone on 2011-06-11
so KDE may be the problem? Any ideas at all?

P.s ive attached the screenshot of the ever climbing memory usage.

Reinstall Kubuntu maybe? in which case any good backup programs?

---

### Post by overtone on 2011-06-17
Solved with a reinstall.

Tried plugging in.out multiple components. Didnt know how to reinstall KDE.

It became unusable.

---

### Post by elianto on 2011-07-02
[SIZE=4][B]this happened to me as well several time
If your disk start behaving crazy on kde startup[/B][/SIZE]
and never ends doing who knows what eating all the memory slowing the interface and bringing your computer to knees [COLOR=Red]no worries[/COLOR] it's **[SIZE=2]akonadi[/SIZE]**.
I have this bug since 10.4 and I think it's triggered when, for some  rare circumstance, kde got  killed in the middle.
The workaround I found it's pretty [COLOR=Magenta]painless[/COLOR][COLOR=Black] : before login switch to a terminal (ctrl+alt+f1) login, rm -rf .config/akonadi[/COLOR] then login as normal (ctrl+alt+f7)
I wonder why this bug it's still here!

next time don't do a reinstall just remove the dir and you are ready again

---

