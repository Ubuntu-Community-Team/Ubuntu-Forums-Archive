---
title: "Would like second opinion on firefox crashes."
date: 2010-07-29
forum: General Help
---

### Post by Darin722 on 2010-07-29
My computer is an amd64.  
Last week while surfing the web using a live cd of Ubuntu 9.10 x 32, firefox started crashing constantly.  

I tried a few other live cd's including 9.04, 9.10, 10.04 and both 64 and 32 bit variants.  Firefox crashed constantly even though I had not yet installed add-ons or plugins such as flash.  Curious note: Firefox on an old backtrack 3 cd did not crash in about 2 hours of use.

I noticed this problem with the live cd's first, but later discovered my installed OS has the same problem.  Firefox now crashes constantly.(6 times just trying to get to this forum)  Also, If I am using openoffice when firefox crashes, openoffice also crashes.  Firefox on the live CDs crash with a segmentation fault and generally firefox will not re-launch.  On the installed OS, firefox will relaunch (updated version)

I have not had any problems with other applications, and I didn't see anything that looked like a problem in dmesg or message logs.

Searching the web for "firefox crash" didn't turn up anything that looked similar.

The live CD's seem to work just fine on my old dell laptop.

so: Does anyone have any suggestions as to how to identify the specific problem? 

So far, it seems to be happening only on my amd64, but I'm not strongly inclined to believe that it is caused by faulty hardware that only affects firefox.

---

### Post by lovinglinux on 2010-07-29
See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by moosabunto on 2010-08-30
> **Darin722 said:**
> My computer is an amd64.  
Last week while surfing the web using a live cd of Ubuntu 9.10 x 32, firefox started crashing constantly.  

I tried a few other live cd's including 9.04, 9.10, 10.04 and both 64 and 32 bit variants.  Firefox crashed constantly even though I had not yet installed add-ons or plugins such as flash.  Curious note: Firefox on an old backtrack 3 cd did not crash in about 2 hours of use.

I noticed this problem with the live cd's first, but later discovered my installed OS has the same problem.  Firefox now crashes constantly.(6 times just trying to get to this forum)  Also, If I am using openoffice when firefox crashes, openoffice also crashes.  Firefox on the live CDs crash with a segmentation fault and generally firefox will not re-launch.  On the installed OS, firefox will relaunch (updated version)

I have not had any problems with other applications, and I didn't see anything that looked like a problem in dmesg or message logs.

Searching the web for "firefox crash" didn't turn up anything that looked similar.

The live CD's seem to work just fine on my old dell laptop.

so: Does anyone have any suggestions as to how to identify the specific problem? 

So far, it seems to be happening only on my amd64, but I'm not strongly inclined to believe that it is caused by faulty hardware that only affects firefox.

I am having the same problem regardless whether I install 10.04 32 or 64 bit version. This happens for me on Intel Core i3 architecture.
In my scenario, the firefox crash may crash the whole desktop environment and reboot is needed,
The closest search yield to this bug: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/626065](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/626065)

Hope it helps

---

