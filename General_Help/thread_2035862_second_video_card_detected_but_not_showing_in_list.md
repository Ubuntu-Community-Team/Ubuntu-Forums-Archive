---
title: "second video card detected but not showing in list."
date: 2012-07-31
forum: General Help
---

### Post by dbaile10 on 2012-07-31
I am attempting to build a machine out of some spare parts and I have a couple old video cards. Each of the video cards works fine by themselves but for some reason won't work simultaneously. Both are standard PCI not onboard or pcix so I'm sure they can work together. 

The output of ```
lspci | grep VGA
``` gives me:
```
01:07.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage 128 RE/SG
01:08.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
```

So both are detected. But when I go to activate my second monitor, it doesn't show up in the list. All i get is:
[IMG]http://i.imgur.com/6UVx9.png[/IMG]

Side note... whats up with it naming the monitor laptop? I'm on a custom built desktop....

Anyhow, thats not the end of the weirdness. If I log in and then log out, the second screen comes on and gives me a bunch of white vertical lines with some text that I can't really make out. It looks like:
[IMG]http://i.imgur.com/HHOCVl.jpg[/IMG]

And if I shut the machine down the splash screen seems to work just fine as well:
[IMG]http://i.imgur.com/s9aj1l.jpg[/IMG]

I have never encountered any problems like this and any help would be greatly appreciated!

---

### Post by Bobhuber on 2012-07-31
I'm not quite sure of what you are trying to do.
Your not going to be able to run 2  different video  cards at the same time. They both require a different set of drivers .

---

### Post by dbaile10 on 2012-07-31
I am trying to run both, is it not possible to run 2 different video cards with linux?

---

### Post by Bobhuber on 2012-07-31
> **dbaile10 said:**
> I am trying to run both, is it not possible to run 2 different video cards with linux?
Nope not in linux or Windows . The key word is different.
If they are the same manufacturer and designed to so it is done quite often. Heres a simple link posted by one of the retailers.
[http://www.overstock.com/guides/How-to-Use-Dual-Video-Cards-for-Your-Gaming-PC](http://www.overstock.com/guides/How-to-Use-Dual-Video-Cards-for-Your-Gaming-PC)

---

