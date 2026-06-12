---
title: "firefox crashed very often in 10.04"
date: 2010-07-29
forum: General Help
---

### Post by srikrishnan on 2010-07-29
Hi All,

In My system I have installed 10.04 Ubuntu 64bit version recently. From the beginning itself, my web browser firefox crashed and disappeared very often in between my surfing, Can anybody help me to solve this problem?

Thanks,
Srikrishnan

---

### Post by TheNerdAL on 2010-07-29
Does it crash when Flash is being used? This might work: [http://ubuntuforums.org/showthread.php?t=1130397](http://ubuntuforums.org/showthread.php?t=1130397)

---

### Post by lovinglinux on 2010-07-29
Does it crash when performing a particular action or viewing a particular content like videos or is it random?

Have you tried to start it in safe mode to see if it is an extension causing this?
Have you tried to create a new profile to see if the problem persists?

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by srikrishnan on 2010-08-02
Hi,

Thanks for your reply.

I came to knew that not only Firefox, many of the applications closes 
automatically in between a process. I dont know about this. I am using 
Ubuntu since version 7. First I have upgraded from 9.04 to 10.04  32 bit 
version, at that time also I found this same problem. So I formatted my 
system and reinstalled fresh version of 10.04 32bit as per the guidance from 
Ubuntu Forum. But again the same problem appears. So at last I reformatted 
my system and reinstalled 10.04 64bit version. Unfortunately again this 
problem occurs. I think there is some problem with this latest version on my 
system. I fed up very much.

I think I have only two choices before me one is to install old version or I 
have to move to some other distro

Thanks,
Srikrishnan

---

### Post by efflandt on 2010-08-02
It could be a problem with older video chip.  Have you tried **nomodeset** kernel boot parameter?

Without that my old desktop with ATI X1300 video was slow and it would not suspend or hibernate.  And my company laptop with Radeon Mobility X1300 would have boot video glitch/hang.  The nomodeset resolved those issues.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

I have an older low end laptop that I inherited when I got someone a new one.  That did not work very well at all with 9.10, dropped keypresses, mouse lag/jumpy, failure to wake from suspend or hibernate.  But it works fine with 10.04.  So some fixes or advancements may work better for some hardware and worse for others.

---

### Post by worksofcraft on 2010-08-02
I too had problems with both Firefox and Google Chrome just exiting for no apparent reason on Lucid Lynx 64 bit.

I installed the latest proprietary driver from Nvidia and the problems ceased :)

Try

System->Administration->Hardware Drivers

Select the latest version then click Activate

---

