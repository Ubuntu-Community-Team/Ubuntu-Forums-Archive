---
title: "Gnome-Do using 100% processor usage on start up"
date: 2010-02-06
forum: General Help
---

### Post by beastrace91 on 2010-02-06
Howdy All,

So I have 64bit Ubuntu 9.10 installed on my laptop and I noticed one day on boot that everything I did was running very slowly. Upon cracking open terminal and running **top** to see what was bogging the system I found that gnome-do was taking up 100% of my processor...

This happens around 50% of the time when I boot I've noticed. Killing the processor and restarting Gnome-Do makes the application behave as it should.

Ideas on why this might be? Just a bad 64bit version in the repos I'm guessing? Might try and compile a new version from source later today.

Regards,
~Jeff

---

### Post by mohitchawla on 2010-02-18
I observed similar behavior today, and it was alarming ! 

I was trying Gnome-Do for the first time, and after random desktop freezes & several routines of stopping & starting GDM manually, I thought I shouldn't try anymore. And then while I was doing normal stuff...browsing etc., suddenly I noticed my CPU temp jump from 25 degrees to 46 degrees ! First I thought my overclock went bad or something, but after checking out the system monitor I saw 4 cores ( 2 physical & 2 logical) being 100 % utilized ! I ended all gnome-do processes, removed it from my system

Well, yeah might just be bad repo version, but really BAD.

---

