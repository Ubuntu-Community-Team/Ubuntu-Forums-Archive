---
title: "Synaptic 404 error"
date: 2009-11-08
forum: General Help
---

### Post by 317070 on 2009-11-08
Hi,

Since I live in Belgium, I have download limits. I can download only 2.5 Gb every month.
What does this mean: well, I can't follow the Ubuntu upgrades coming out regulary, so now I'm stuck on Gutsy Gibbon 7.10 Ubuntu. I'm pretty OK with this, if only synaptic would continue working...

Does anyone know how I could set things in synaptic so it would continue to allow me to download certain packages of software? Similar with apt-get, etc...
(Oh, and I'm pretty noobish in Linux, not very, but pretty :D)
Now it gives:
[INDENT][http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found
[http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found
.... (long list)
[/INDENT]If anyone could help me with this small issue, I would be very grateful. Also, please ask me if you need additional information. I will supply it.

Cheers,

Jonas

---

### Post by chriskin on 2009-11-08
i think that 7.10 is no longer supported since april - might be the reason.
or i might be wrong
i would definitely use a more modern release though if i were you, the 9.10 for example is a fine release, or at least the 8.04 that is LTS and will keep being supported for a loong time

---

### Post by 317070 on 2009-11-08
And how would I update?

Going directly to 9.10 means reconfiguring everything from scratch. (and having no internet for half a month)
Going to upgrade 1 by 1 means having no internet for 5 months...

:confused:

Is there no solution that does not involve losing my internet?

And how long is LTS?

---

### Post by wojox on 2009-11-08
Ya, chriskin is right you'll need to find something more recent.

---

### Post by wojox on 2009-11-08
Is there any other place you can download from and try something like APTonCD?

---

### Post by chriskin on 2009-11-08
> **317070 said:**
> And how would I update?

**_Going directly to 9.10 means reconfiguring everything from scratch. (and having no internet for half a month)_**
[I]Going to upgrade 1 by 1 means having no internet for 5 months...
[/I]
:confused:

Is there no solution that does not involve losing my internet?

And how long is LTS?

[B][U]why is that going to happen if you install 9.10???
[/U][/B]

[I]and why is that going to happen if you upgrade?!?
[/I]

i thought belgium was a place of High download speeds and no limits, like the rest of the western europe (or am i just hoping for too much? we got 20-25mbps and no limits in greece , and everyone knows that we are always really back on technology)

---

### Post by chriskin on 2009-11-08
> **wojox said:**
> Is there any other place you can download from and try something like APTonCD?

you can also request a free cd from ubuntu's site to be sent to you

> **317070 said:**
> And how would I update?

Going directly to 9.10 means reconfiguring everything from scratch. (and having no internet for half a month)
Going to upgrade 1 by 1 means having no internet for 5 months...

:confused:

Is there no solution that does not involve losing my internet?

And how long is LTS?


both 8.04 and 9.10 have end of support at april 2011
10.04 will most probably be LTS as well, having support till 2013 - after the world gets destroyed :)

wikipedia also says 
> After each version of Ubuntu has reached its end-of-life time, its repositories are removed from the main Ubuntu servers and consequently the mirrors.[94] However, older versions of Ubuntu repositories can be found at old-releases.ubuntu.com. [95]

check the last part with the old repositories if you want to stay at good old 7.10

---

### Post by 317070 on 2009-11-08
> **chriskin said:**
> [B][U]why is that going to happen if you install 9.10???
[/U][/B]

[I]and why is that going to happen if you upgrade?!?
[/I]

i thought belgium was a place of High download speeds and no limits, like the rest of the western europe (or am i just hoping for too much? we got 20-25mbps and no limits in greece , and everyone knows that we are always really back on technology)
Bad liberating of the telecom-market by our government, combined with being a poor student in an overpopulated university? 

Back on topic:
So I could update from 7.10 directly to the latest version, if I only had the CD?
So this would work: [https://help.ubuntu.com/community/KarmicUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD]("https://help.ubuntu.com/community/KarmicUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD")
Or would I need to install all intermediate versions, or fear for my computer to stop rebooting ever again?:confused:

Oh, could you provide me a link to that text you quoted, I guess that's exactly what I need :D

---

### Post by chriskin on 2009-11-08
i haven't tried upgrading (ever!) since i think of new releases as an opportunity to set everything up once again, the way i would like it that time :)check google or wait for another answer, i think you would either upgrade one after another or go to a clean install - i have no proof at all for that though

---

### Post by 317070 on 2009-11-08
> **chriskin said:**
> i haven't tried upgrading (ever!) since i think of new releases as an opportunity to set everything up once again, the way i would like it that time :)check google or wait for another answer, i think you would either upgrade one after another or go to a clean install - i have no proof at all for that though
Do you then need to redownload all software (like VLC, compiz, ...) and all those others again? Or is there a way to keep them (and my documents of course) and still reinstall?

Thanks for being so helpful btw, 

If there is anyone else having a solution, be sure to let me know :)

---

