---
title: "Natty compiz in Gnome-classic"
date: 2011-04-15
forum: General Help
---

### Post by chrroessner on 2011-04-15
Hi,

just a short question: I enabled the "negative"-plugin in compiz in Natty, because I need it (visual impairment). While in Maverick full screen invert mode worked fine, it does not do so in Natty.

It inverts the whole X-server, but when you click a pull-down menu, this one is not inverted. If you open new windows, they all are not inverted.

I have:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

In compiz:

Neg Windows: any
Exclude Windows: type=Desktop

This is the same as in Maverick. Did something change in Natty? What could I set to fix this problem?

Working without this plugin, it is very hard for me :-(

Thanks in advance

Christian

---

### Post by wilee-nilee on 2011-04-15
> **chrroessner said:**
> Hi,

just a short question: I enabled the "negative"-plugin in compiz in Natty, because I need it (visual impairment). While in Maverick full screen invert mode worked fine, it does not do so in Natty.

It inverts the whole X-server, but when you click a pull-down menu, this one is not inverted. If you open new windows, they all are not inverted.

I have:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

In compiz:

Neg Windows: any
Exclude Windows: type=Desktop

This is the same as in Maverick. Did something change in Natty? What could I set to fix this problem?

Working without this plugin, it is very hard for me :-(

Thanks in advance

Christian

Foe all general purposes I have found the xubuntu version of natty easier to set the compiz settings with, and just use over all, you might put it on a thumb with persistence and test out the compiz, hope you get it sorted out.

---

### Post by chrroessner on 2011-04-15
Well, I already use the compiz configuration manager(ccsm), which gives me full control over compiz. Yet I am unsure, if something has changed in compiz and this is a regression bug. Might have to do with Unity<->compiz modifications. Yet I dont know much about the new desktop and its components. I simply chaned gdm to give me back Gnome-classic.

Does someone else have any ideas. Or even could confirm my problem? Maybe it also might have to do with the i5-CPUs intgrated iGPU. Formerly I used my ATI 6850 with official drivers from the website

Thanks
Christian

---

### Post by chrroessner on 2011-04-19
Okay, it has nothing to do with the iGPU. My Radeon HD6850 shows the same results.

Nobody any idea? Am I the only person with visual impairment?

---

### Post by mastablasta on 2011-04-19
Natty is not out yet. so you should report this to whoever is fixing bugs.

---

### Post by chrroessner on 2011-04-19
So you guess this is a bug and not a settings problem? I was unsure, if it is a bug. I thought it might also be possible that I need to change some configuration settings anywhere.

N.B.: I posted this as a bug report before coming here to the forum. My fear is that this bug will not be fixed, because the majority of users does not even know about some plugins like the one I spoke about. So it probably has a very low priority (what I can understand, too).

---

