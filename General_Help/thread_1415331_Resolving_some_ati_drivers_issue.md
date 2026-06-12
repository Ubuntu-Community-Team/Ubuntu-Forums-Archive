---
title: "Resolving some ati drivers issue"
date: 2010-02-24
forum: General Help
---

### Post by Struki on 2010-02-24
I'm trying to fix this problem: [http://ubuntuforums.org/showthread.php?t=1402806](http://ubuntuforums.org/showthread.php?t=1402806)

But since all my post here are not helping me , i turned to launchpad and found something similar, bit i need some help explaining what are they talking about, specifically:

[I]I have a problem with fglrx driver since Catalyst 9.9.
After installation and reboot I get only black screen **when X tries to start** and keyboard doesn't work however when I press power button then the system shuts down properly after a while.
I have noticed this for the first time on Hardy after installing Catalyst 9.9 and since then I have the same problem on Karmic and Catalyst 9.10/9.11 as well.[/I]   

I don't understand the bold text, What is this X he's talking about?

---

### Post by Ozymandias_117 on 2010-02-24
X is a program that runs your GUI. There are multiple desktop managers that run on X, such as Gnome (Default for Ubuntu) KDE (Default for Kubuntu) Xfce (Default for Xubuntu) and others such as Fluxbox

---

### Post by drdanielfc on 2010-02-24
would you mind pointing out which ati card you have (ie radeon x1600)?

---

### Post by Struki on 2010-02-25
My hardware is listed in my sig, radeon HD 3200

---

### Post by Struki on 2010-02-25
> **Ozymandias_117 said:**
> X is a program that runs your GUI. There are multiple desktop managers that run on X, such as Gnome (Default for Ubuntu) KDE (Default for Kubuntu) Xfce (Default for Xubuntu) and others such as Fluxbox

yea i figured as much, just wanted to be sure, thnx!

---

### Post by drdanielfc on 2010-02-25
> **Struki said:**
> My hardware is listed in my sig, radeon HD 3200

Sorry, didnt notice that. Is using the default drivers an option or do they not work properly? Also, you may want to try the instructions at [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by lavinog on 2010-02-25
The radeon HD 3200 should work fine with the proprietary drivers offered with ubuntu.
The opensource drivers should work also, but without 3d support.

---

### Post by Struki on 2010-03-03
It seems I have resolved my problem, anyone intersted can read about it here: [http://ubuntuforums.org/showthread.php?p=8909295#post8909295](http://ubuntuforums.org/showthread.php?p=8909295#post8909295).

---

