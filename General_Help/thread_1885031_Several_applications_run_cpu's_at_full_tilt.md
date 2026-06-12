---
title: "Several applications run cpu's at full tilt"
date: 2011-11-22
forum: General Help
---

### Post by cackerso on 2011-11-22
I recently upgraded to 11.10 from 11.04.  Now Firefox, Gimp, Adobe Reader, and Truecrypt all maxout the cpu's when they are running.  There may be others but those are what I know of for the moment.  I have an AMD dual core 3000 processor.  This seems like some fundamental bug in Kubuntu.

---

### Post by gordintoronto on 2011-11-22
How are you measuring the CPU usage? There are reports that System Monitor itself maxes out the CPU under certain circumstances, which are not well understood.

If you open a Terminal and enter the command top, you might get a vastly different view.

---

### Post by cackerso on 2011-11-23
I'm using Conky.  So I can easily see the different cpu use by different applications.  Top run in a terminal gives me the same result as the measurement by Conky.

---

### Post by Bobhuber on 2011-11-23
> **cackerso said:**
> I recently upgraded to 11.10 from 11.04.  Now Firefox, Gimp, Adobe Reader, and Truecrypt all maxout the cpu's when they are running.  There may be others but those are what I know of for the moment.  I have an AMD dual core 3000 processor.  This seems like some fundamental bug in Kubuntu.
What video card and driver. ? I had the same problem with the system monitor pushing one of my CPU'S to 100%  as stated and found that the nvidia 290.10 drivers were causing the trouble. Downgraded to 285-05-09 and all is well again.

---

### Post by oldtimer7777 on 2011-11-23
> **Bobhuber said:**
> What video card and driver. ? I had the same problem with the system monitor pushing one of my CPU'S to 100%  as stated and found that the nvidia 290.10 drivers were causing the trouble. Downgraded to 285-05-09 and all is well again.

Disable compiz compositing for now, and try a couple of different video drivers like above.

---

### Post by cackerso on 2011-11-26
My card is a GTX 560.  The driver, according to the Nvidia X server settings app is 280.13.

I didn't know I had compriz enabled.  In Settings > Stystem settings > Desktop effects > General, I have "enable desktop effects at startup" un checked.  So when I read the posts here I looked at absolute beginners talk and after some reading, installed ComprizConfig Settings Manager.  Every time I try to uncheck the compositing box it crashes.

Also it isn't obvious to me how to pick the video driver installed.  I assume there is some way around the "Additional Arivers" app.

---

### Post by Bobhuber on 2011-11-26
> **cackerso said:**
> My card is a GTX 560.  The driver, according to the Nvidia X server settings app is 280.13.

I didn't know I had compriz enabled.  In Settings > Stystem settings > Desktop effects > General, I have "enable desktop effects at startup" un checked.  So when I read the posts here I looked at absolute beginners talk and after some reading, installed ComprizConfig Settings Manager.  Every time I try to uncheck the compositing box it crashes.

Also it isn't obvious to me how to pick the video driver installed.  I assume there is some way around the "Additional Arivers" app.
OK - You don't want or need compiz in 11.10 Oneiric.The video card you have should work fine with the drivers you have installed . I would not recommend updating to the latest Nvida drivers (290.10) untill they get all the bugs worked out. As far as CPU usage I have no easy answer. If you updated from 11.04 instead of a fresh install it's going to be really difficult to tell whats going on if its doing it in more than one app.
The first thing I would look at is the Java and flash drivers. Sorry I could not be of more help.
Correction 0n the compiz statement. It depends on the DE you are using. I'm using gnome3 and no compiz or Unity at all.

---

### Post by cackerso on 2011-11-29
It seems to me that it should make it easier if it affects a few but not all applications.  That means it's not specific to one.  

So how do I proceed to figure out whats wrong?

Second, it's not obvious from the last post how exactly I tell if compriz is on or off.

---

### Post by cackerso on 2011-12-08
OK, I got some expert help elsewhere.  So in case this affects anyone else I'll post the solution here.

In 11.04 the Desktop Appearance was set to oxygen-molecule GTK+.  I changed this in one of the system settings like 'Style" to another theme.  But this didn't remove the theme from other settings like 'Colors'.  When I upgraded to 11.10 these left over settings  caused the problem.  As soon as I purged all instances of oxygen-molecule from my Desktop Appearance the problem went away.

It had nothing to do with Compriz.

---

