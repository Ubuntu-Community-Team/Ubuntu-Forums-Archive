---
title: "Upgrade to Karmic Koala broke Eclipse"
date: 2009-11-13
forum: General Help
---

### Post by schallstrom on 2009-11-13
Hi,

since the upgrade to Karmic Koala, Eclipse shows some odd behavior on my Thinkpad X60 (Core Duo, 32 bit CPU): The "Next" and "Finish" Buttons in Wizards (e.g. the "New Project" Wizard) do not work when just clicking on them. One has to press enter to get to the next dialogue. Or when I choose a software repository in the "Install New Software" menu, the available software packages only show up when I resize the window (I think because the content gets redrawn then). As you see: It's nothing that totally stops me from working, but it's very annoying.

Oh, and I did not install Eclipse through the Ubuntu repository but downloaded it directly from eclipse.org. So it cannot be a bug in Eclipse itself. It must be the Java version used in Karmic Koala that introduced the flawed behavior. I also only have the official Sun Java installed.

Does anyone have the same problem and knows a proper fix?

---

### Post by jackcholt on 2009-11-13
I installed Karmic as a new install and have installed various versions of Eclipse since.  I find that if I install Eclipse directly from Eclipse.org I have the same problems and installing new plugins is next to impossible because the text of the items included in the plugins doesn't appear correctly and it is difficult to see what is included in order to install them.

The Ubuntu team for Eclipse probably know this already however, because I also installed Eclipse through the Ubuntu software center and it doesn't have those problems.  

The official Ubuntu release has other problems though because adding any additional plugins is difficult because it is next to impossible to figure out where to go for standard plugins like EMF that form the basis for other plugins I would like to add like m2eclipse and subclipse.

---

### Post by schallstrom on 2009-11-13
> **jackcholt said:**
> 
The official Ubuntu release has other problems though because adding any additional plugins is difficult because it is next to impossible to figure out where to go for standard plugins like EMF that form the basis for other plugins I would like to add like m2eclipse and subclipse.

Thanks for replying. I store all my code in a Subversion repo, so installing Subclipse is absolutely necessary, without it, Eclipse would be almost without any use for me. So installing Eclipse from the Ubuntu repos does not seem to be an option, either.

By the way: This is not an Ubuntu-exclusive problem. I have a number of fellow students who experience exactly the same problem using other Distros like Arch, Gentoo and alike. I really looks like a bug in Java.

---

