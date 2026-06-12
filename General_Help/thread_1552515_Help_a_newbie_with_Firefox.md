---
title: "Help a newbie with Firefox"
date: 2010-08-13
forum: General Help
---

### Post by aitchondo on 2010-08-13
I may be old to the world, but I am new to computers and ubuntu. I have a 64 bit system that runs windows 7 and unbuntu. Up until a few days ago, when it was updated, Firefox ran great under unbuntu. Now, when I hit the icon to start it, nothing. Nothing. I am worldly smart, but I may be lacking in some computer skills, so be gentle. Give me something to start with please. Thank you,
Aitchondo:confused:

---

### Post by [Shawn] on 2010-08-13
> **aitchondo said:**
> I may be old to the world, but I am new to computers and ubuntu. I have a 64 bit system that runs windows 7 and unbuntu. Up until a few days ago, when it was updated, Firefox ran great under unbuntu. Now, when I hit the icon to start it, nothing. Nothing. I am worldly smart, but I may be lacking in some computer skills, so be gentle. Give me something to start with please. Thank you,
Aitchondo:confused:
Hi.
You can try to run firefox in safemode and see If that correct's the issue. Go to terminal
Applications>Accessories>Terminal
And type this ```
firefox -safe-mode
```
And then check the boxes and click continue in safemode.
Hope this helps!

---

### Post by lovinglinux on 2010-08-13
Try to delete the files **compatibility.ini** and **secmod.db** from your FF profile folder, located under ~/.mozilla/firefox/<defaultprofile>

If that helps but the problem comes back later, then use my extension [ProfileCleaner]("http://profilecleaner-extension.blogspot.com/") to remove those files automatically when Firefox exits.

If that doesn't help, then see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by aitchondo on 2010-08-14
tried it, got a "segmentation fault" message. (the firefox -safe-mode) thing.Thanks anyway. The deleted compatibility.ini and secmod.db and when I hit the FF icon, still nothing, not even a message. Thanks again. Will now try the General Troubleshooting Steps tutorial and FF4 support thread:faq, how to install, optimize, customize...
Thanks again,
Aitchondo (pronounced Hondo)

Back again. Got it up. Had to create a new profile. Thanks again, Shawn and lovinglinux. Appreciate all the help.
Aitchondo

---

