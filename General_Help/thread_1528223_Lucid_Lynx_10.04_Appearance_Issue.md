---
title: "Lucid Lynx 10.04 Appearance Issue"
date: 2010-07-10
forum: General Help
---

### Post by skarme on 2010-07-10
This is a problem I have occasionally. The bar above the menu bar(menu bar: with drop down headers as file, edit, view, etc) i.e the one containing the minimize, maximize and close button doesn't appear. When I restart the PC, everything becomes alright. I would like to reiterate that this happens sometimes, it's not a everyday issue. Is this an idiosyncrasy of the OS on my PC only or are others facing the same issue. Any way to permanently get rid of this would be nice.

---

### Post by dino99 on 2010-07-10
you can hunt errors logged into .xsession-errors (/home, ctrl+h) and into : system admin logviewer

does this issue is only with a specific theme or with any ?

sudo dpkg-reconfigure metacity

sudo apt-get update
sudo apt-get install -f

---

### Post by skarme on 2010-07-10
> **dino99 said:**
> 

does this issue is only with a specific theme or with any ?


I haven't used all that many themes on this version of Ubuntu, just 2-3 I believe. And yes, it's been an issue with each one of them

---

### Post by dino99 on 2010-07-10
so reconfigure metacity and look for usefull errors logged into .xsession-errors (/home, ctrl+h) and into : system admin logviewer

---

### Post by jimbop99 on 2010-07-10
I encountered this same problem and it seems to be tied in with Compiz. I love to play around with all the settings. Long story short. I installed Simple CompizConfig Settings Manager and so far the Title bar has been behaving. I first went into visual settings and set it to none and when I had my title bar back then I changed my settings in Simple Compiz.

---

### Post by CoolJohnB on 2010-07-10
I had the same problem, I just right clicked the title bar and put a tick in the "lock to panel" box, that solved the problem, it now stays permanently.

---

### Post by intheflesh on 2010-07-10
It happens to me sometimes, too. I keep a shortcut to metacity on desktop, just in case. I suppose you could add **[FONT=Courier New]compiz --replace[/FONT]** (or **[FONT=Courier New]metacity --replace[/FONT]** if you use that) to System -> Preferences -> Startup Applications just to be sure.

---

### Post by skarme on 2010-07-10
> **CoolJohnB said:**
> I had the same problem, I just right clicked the title bar and put a tick in the "lock to panel" box, that solved the problem, it now stays permanently.
You mean 'Always on Top' check box?

---

