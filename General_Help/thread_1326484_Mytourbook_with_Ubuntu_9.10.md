---
title: "Mytourbook with Ubuntu 9.10"
date: 2009-11-14
forum: General Help
---

### Post by lars.modig on 2009-11-14
Hello,

I've running Mytourbook since ubuntu 8.10 and it has worked like a charm at every upgrade...

However now when upgrading to 9.10 the graph has disaper. I can view the statistics the tour but the altitude heartbeat and so on is invisible except where the slider is. There you see one point of the graph. So if I drag it through the time slide I can see the graph going up and down, but ...

Is there anyone that have had the same issue? Anyone who has an idea how to correct this. I really would like to stick to this software as I see as the best GPL software for GPS logging.

A second question, do someone know if you could sync the database file with UbuntuOne so that you could run Mytourbook from different computers?

Thanks,

Lars

---

### Post by daniel.schudel on 2009-11-18
> **lars.modig said:**
> 
However now when upgrading to 9.10 the graph has disaper. I can view the statistics the tour but the altitude heartbeat and so on is invisible except where the slider is. There you see one point of the graph. So if I drag it through the time slide I can see the graph going up and down, but ...

Is there anyone that have had the same issue? Anyone who has an idea how to correct this. I really would like to stick to this software as I see as the best GPL software for GPS logging.


I'm just chiming in with a "Me Too".  My Jaunty installation displays the profiles correctly, but my Karmic has the exact symptom you describe (two different machines).

I've asked the same question on the Ubuntu-cyclist mailing list - perhaps someone will have an idea there - [https://lists.launchpad.net/ubuntu-cyclists/msg00110.html](https://lists.launchpad.net/ubuntu-cyclists/msg00110.html)

Daniel

---

### Post by daniel.schudel on 2009-11-18
See this link - I have not tried it yet:

[https://sourceforge.net/projects/mytourbook/forums/forum/622811/topic/3459086](https://sourceforge.net/projects/mytourbook/forums/forum/622811/topic/3459086)

---

### Post by fep1343 on 2009-11-21
Hi

After upgrading to Ubuntu 9.10 I had the same problem with Mytourbook & sporttrack. The graphs disappeared & my tours became invisible.The problem comes from an intel driver in some notebooks. I updated to the latest intel-driver found in Tormod Voldens PPA repository & it worked for me.

Tech details:

1-Add this 

```
ppa:xorg-edgers/ppa
```
to your system's Software Sources via synaptic package manager & reload repository in synaptic.

2- In synaptic package manager find & mark libdrm-intel1 and xserver-xorg-video-intel for update. Install them only by synaptic package manager. 
Dont use update manager for this operation if not other unnecessary packages will be also installed. 3. restart

---

### Post by daniel.schudel on 2009-11-30
Thanks fep1343 - works great now!

---

