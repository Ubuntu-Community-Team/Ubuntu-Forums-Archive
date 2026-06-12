---
title: "How to Restore the &quot;MeMenu&quot;"
date: 2010-03-14
forum: General Help
---

### Post by brockangelo on 2010-03-14
Does anyone know how to get this back? I started using 10.04 this weekend and was playing around with the new "MeMenu" and removed it from the menu bar. Now I can't seem to get it back. Its not found when I try to add to the panel and it isn't part of the Gwibber app anywhere either.

Or is there a way to just restore the bar to its default? I lost my logoff/shutdown menu button on the far right when I did that too.

---

### Post by CompyTheInsane on 2010-03-15
The MeMenu can be found inside the applet called 'Indicator Applet Session'.
Do you see that in the Add To Panel window?

---

### Post by brockangelo on 2010-03-15
That was it! Thank you compugeek32!

---

### Post by budhajeewa on 2010-03-21
> **compugeek32 said:**
> The MeMenu can be found inside the applet called 'Indicator Applet Session'.
Do you see that in the Add To Panel window?

In my case, "Indicator Applet Session" thing don't have the MeMenu in it!

Even though I've updated Ubuntu few time since MeMenu got lost from the panel, nothing restored it back! :O

---

### Post by howefield on 2010-03-21
> **budhajeewa said:**
> Even though I've updated Ubuntu few time since MeMenu got lost from the panel, nothing restored it back! :O

Have you checked that the indicator-me package is still installed ?

If it shows as installed, try marking it for reinstallation.

---

### Post by budhajeewa on 2010-03-22
Installing indicator-me package solved the problem.

But I'm not sure how it got removed, and that caused me another problem, which I've posted in following thread:

[http://ubuntuforums.org/showthread.php?p=9007447](http://ubuntuforums.org/showthread.php?p=9007447)

---

### Post by blackmars0 on 2010-04-30
I had this same issue after accidentally removing the Indicator-me from the panel. 

I fixed it through the following steps: 

[INDENT]1. Open Synaptic package manager. 

2. Search for Indicator-me

3. Mark the Indicator-me package for re-installation. 

4. Once the package is reinstalled, add the Indicator applet back onto your panel bar. [/INDENT]


Hopefully that helps someone out there who did the same thing I did.

---

### Post by RobJN on 2010-05-30
Ok so I'm another silly newbie (well trying Ubuntu again) and removed this too. Have managed to add it back but in the wrong place. 

How do you move things on the panel? Edit: Sorted. Needed to unlock all the other items so i could move it past them back to the rhs.

---

