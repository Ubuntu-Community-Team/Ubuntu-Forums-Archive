---
title: "Graphics problems in Google Earth?"
date: 2009-08-07
forum: General Help
---

### Post by T.R. on 2009-08-07
Google Earth is acting up for me suddenly. It worked perfectly last time I used it (about 2 days ago), but now drop-down menus don't show any options other than the one my pointer is on, and when I click on placemarks the text either flashes briefly and then disappears, or never shows up at all.

I've tried a few things, from deleting GE's cache, to a complete reinstall of GE. Nothing fixed the problem.

When I run in terminal, I get the output ```
undefined:4: Can't find variable: ge_bridge 
```whenever I try to click on a placemark. There's also a "file" called "instance-running-lock" in /home/[my username]/.googleearth, which is locked and broken, and which I assume is related to the problem. It comes back when I try to start GE after I delete it.

At first I thought it might have been caused by my installing the screenlets plugin, but I doubt the two applications could possibly interact like that. Nothing else is broken (that I know of).

I'm running fully updated Jaunty on a Thinkpad R61e, Graphics card is Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller.

---

### Post by sandman55 on 2009-08-08
I have been trying to get Google Earth from Medibuntu via Synaptec package manager going for a while. I have even tried reinstalling Jaunty and trying again (Google Earth is presently uninstalled) What I have found is google earth seems to work but when I go to the menus they flash on and off and so does the prompts that give the tips when GE starts

EDIT: I am wondering if installing an earlier version of GE would do the trick.

---

### Post by T.R. on 2009-08-09
I think it may be an update that is causing the problems, but Google Earth's EULA basically forces you to automatically request and receive updates. I don't know of any way to use an older version of GE without it automatically upgrading to the most recent.

---

### Post by sandman55 on 2009-08-10
I have recently reinstalled GE and it is still the same I wonder if it is that I havent installed drivers for my Radeon 9600 graphics card. I have read a little about it on some threads and one guy said about ATI cards being a problem.

---

### Post by stinger30au on 2009-08-10
> **sandman55 said:**
> I have recently reinstalled GE and it is still the same I wonder if it is that I havent installed drivers for my Radeon 9600 graphics card. I have read a little about it on some threads and one guy said about ATI cards being a problem.

do you have a mates pc handy who has a different video card you can swap and test with?

---

### Post by sandman55 on 2009-08-10
I have an old AMD duron PC with a very basic pci video card but I don't want to put it in this PC because I don't want to mess with the windowsXP drivers

---

### Post by T.R. on 2009-10-19
I ended up uninstalling GE completely soon after posting this. Just reinstalled now, and the problem is still there, and I see the same error message.

---

### Post by scouser73 on 2009-10-20
I think that if you delete the Google Earth profile by going to **/home/yourname** pressing **CTRL & H** to reveal the hidden folders and deleting the folder labelled **.googleearth**, then starting Google Earth again, it might work without any problems.

---

### Post by bro brian on 2009-10-21
Hello all -
may I ask - From the Synaptic Package Manager section:
Which Google Earth could I choose between the 3 listed?
Attached is a snapshot of the 3 listed in Synaptic.
Thanks in advance.

---

### Post by T.R. on 2009-11-25
I'd go with googleearth-package of the three, although when I had it I got it from Google Earth's download page.

---

### Post by bro brian on 2009-11-25
I downloaded it, and it seems to be working alright. Thanks!

---

