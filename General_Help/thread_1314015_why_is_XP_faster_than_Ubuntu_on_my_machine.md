---
title: "why is XP faster than Ubuntu on my machine?"
date: 2009-11-04
forum: General Help
---

### Post by ayet on 2009-11-04
my pc specs:
p3 1.2ghz
2x 256mb sdram
1x 128mb sdram
128mb radeon 64bit
tualatin mobo
80gb seagate PATA hdd

i dual boot it on XP and ubuntu, somehow xp seems faster when running all things, why?

---

### Post by t0p on 2009-11-04
It could be a variety of things.  Perhaps some of the hardware drivers used by XP are better than the corresponding drivers in Ubuntu.  Perhaps it's because application X under XP is faster than the corresponding application under Ubuntu.  Etc etc...

Your question is extremely vague - you don't specify which apps are faster, under what circumstances, and so on - so my answer is also vague.  A more precise question may bring forth a more precise answer.

---

### Post by P4man on 2009-11-04
+1 what the above poster said

But to keep in general terms, a fresh install of XP will give ubuntu a run for its money when it comes to speed on just about any machine. 6 months of use and 3 service packs and 12574 windows updates later however, things will probably look dramatically different.

---

### Post by ayet on 2009-11-04
iam just using firefox on both OS's its slower, even browsing files takes longer on ubuntu, i noticed this when i used my p3 machine, this things are not noticeable on my faster system.

iam using ubuntu 8.04 with no compiz or any spacial effects

---

### Post by ayet on 2009-11-04
maybe its just my machine

---

### Post by HiImTye on 2009-11-04
my guess is a hardware issue. hardware issues tend to result in slower performance much more than the operating system or any programs. start by posting your specs and what programs you run on ubuntu (including any you added to start-up)

what is faster in XP than Ubuntu?

in my experience Ubuntu is faster than XP on every computer I've used it on, the only time XP is faster is on program load because of the vast amount of libraries XP loads *at all times*.

---

### Post by ayet on 2009-11-04
> **HiImTye said:**
> my guess is a hardware issue. hardware issues tend to result in slower performance much more than the operating system or any programs. start by posting your specs and what programs you run on ubuntu (including any you added to start-up)

what is faster in XP than Ubuntu?

in my experience Ubuntu is faster than XP on every computer I've used it on, the only time XP is faster is on program load because of the vast amount of libraries XP loads *at all times*.

is there a command i can run maybe on terminal to view all these specs and programs that run on startup so that i can show you?

---

### Post by kio_http on 2009-11-04
Try installing the latest Ubuntu 9.10 Karmic (not netbook edition) Its ultra fast and has been designed for speed so I guess it will improve your system performance

---

### Post by Mighty_Joe on 2009-11-04
Keep in mind that your computer has some weak components compared to current computers.  XP was released 8 years ago, and was designed to run on hardware of that era.  The current release of Ubuntu is intended to run on current hardware and compete with the likes of Windows Vista.  Would you try running Vista on your hardware?
Linux *can *be stripped down to run on older hardware.  Ubuntu is *not *a stripped down Linux.

---

### Post by ayet on 2009-11-04
> **Mighty_Joe said:**
> Keep in mind that your computer has some weak components compared to current computers.  XP was released 8 years ago, and was designed to run on hardware of that era.  The current release of Ubuntu is intended to run on current hardware and compete with the likes of Windows Vista.  Would you try running Vista on your hardware?
Linux *can *be stripped down to run on older hardware.  Ubuntu is *not *a stripped down Linux.

nicely explained, i get it now, so its xp only for my p3 machine then, but i will still try running Ubuntu 9.10 Karmic just to see.

---

### Post by wildweathel on 2009-11-04
XP has lower system requirements, thus it's faster.  XP is also much older, has a less-secure design, and has an obnoxious tendency to slow down with age (especially if it accumulates crapware and viruses).  Really, it's about design trade-offs.  If you have a need for speed on old hardware, Ubuntu isn't the absolute-best choice.  Maybe Gentoo or Slack and a *lot* of effort.  If you can keep it clean--a big 'if'--XP edges out ahead of Ubuntu.  

Turning on minimal desk stop effects might actually make your system faster because it uses your otherwise-idle video processor to handle graphics-processing chores.  

Try [installing xubuntu ]("http://www.xubuntu.org/get")(instructions bottom of page).  You don't have to dual-boot just install a different set of "lighter-weight" desktop programs, log out of the default (Gnome) and into the lighter-weight XFCE.  This is one of my personal favorite tweak for older (and even new systems, I'm thinking of trying it *now* actually and seeing if I can get some quantifiable results of XFCE vs Gnome).

Performance is both subjective and hardware-dependent.  The best choice depends on your personal preferences and your specific computer.  Thus, I have no firm answers for you, only guesses.  Go forth.  Experiment, keeping track of what you did, quantitative observation, seeking illuminating questions, in short, the *real* [scientific approach]("http://www.eskimo.com/%7Ebillb/miscon/miscon4.html#meth") is the key to getting the most out of your computer.  That's the same in any performance hobby, whether cars, computers, or [clothes-irons]("http://www.google.com/search?q=extreme+ironing").

---

### Post by HiImTye on 2009-11-04
```
apt-get install gnome-device-manager
```
will install the 'device manager (system tools>device manager)

-this will give you a hardware list

for startup I dont know of a reliable way to display all of the startup apps/services

perhaps someone else knows

---

### Post by HiImTye on 2009-11-04
now that I think about it youre using a pIII and they tend to slow down due to graphics. ca you run xcompmgr? (sudo apt-get install xcompmgr)

check if you can use DRI (you may need to use a custom built driver)

---

### Post by P4man on 2009-11-04
All the theory aside, its of course entirely possible the OP has a performance issue due to bad or no videodriver or a process hogging his cpu and ram.

To the OP: open a terminal and type 

```
top
```

Copy paste the output here.
Also check if videohardware acceleration is enabled. Try running ```
glxgears -info
``` or something
 (probably someone knows a better test)

---

