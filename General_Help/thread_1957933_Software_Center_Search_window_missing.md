---
title: "Software Center Search window missing?"
date: 2012-04-13
forum: General Help
---

### Post by maureenc on 2012-04-13
Hi,
I'm running Oneiric 11.10 using the  2.6.38-1001 kernel built for the Tegra Toshiba AC100. With Classic Gnome and LightDM desktop.

When I go to the Ubuntu Software Center..... After waiting about ten minutes while it eventually loads...... I don't have any facility to search for a specific package.

I'm sure I have seen screenshots where there is a search window in the top right-hand corner..... Mine only has the > < arrows and the logos for "All software", "Installed" and "History". Nowhere to enter anything.

If I go into "Edit" there is an option to Search but nowhere to enter any search criteria.

I have Synaptic installed and that loads reasonably quickly but I find the reviews useful sometimes.

Have I just got a duff version? 

Any help would be much appreciated.

---

### Post by raja.genupula on 2012-04-13
While i am using Gnome-shell and unity i too have faced this issue .its about gnome theme . change the theme .

---

### Post by maureenc on 2012-04-13
Thank you for responding Raja..

Unfortunately I can't change the Theme.... I can't  install Tweak Tool or Gnome Shell... When I try to install them each says I need the other as they are dependent.... But I can't install either.

I have Gnome-session and gnome-fallback installed so maybe there is something there that is screwing things up?

---

### Post by raja.genupula on 2012-04-13
```
sudo apt-get install -f
```

---

### Post by maureenc on 2012-04-13
I had already done that Raja via Synaptic and again in command line...

Apt-get check returned nothing either....

---

### Post by raja.genupula on 2012-04-14
you do have Unity desktop also right , now do as boot with unity and look at there in Software center . 

if search box now visisble we need to think , if its not found then right click on the desktop and change the theme from there and again open the SC again . 


Hope that helps :)

---

### Post by maureenc on 2012-04-14
Hi Raja,

I finally managed to get Tweak Tool and themes installed..... There was a conflict of versions with one of the icon theme packages that had originally been installed with the 11.10 kernel so I had to force Synaptic to revert to the older version and the install went ahead.

I wish it hadn't worked though because to install Tweak Tool I ended up with Gnome Shell and 39MB of stuff I don't want! I don't know why this is always the case with Ubuntu? You want something small and you end up with a huge overhead.... Also when trying to uninstall one small item you need to remove loads of things you want to keep.

Anyway.... It didn't make any difference except that it slowed my little netbook down to a crawl.... I had spent the past few weeks tweaking it so that I got rid of most of the "fat"..... 

I've done apt-get remove Gnome Tweak Tool to try to get back to where I was before but the only thing it took with it was the Gnome Shell itself! Only 5.38KB of the 39MB it installed originally and I still have all of the garbage it installed with it!

Does anyone understand the logic of this? 

If I do an apt-get purge on the tweak now, do you think it will get rid of the other stuff?

I will take a break from it over the weekend and try it with Unity as you suggest early next week.... 

Thanks for your help Raja.... Have a good weekend

---

### Post by maureenc on 2012-04-16
I've purged and run an autoremove and the machine is back to normal again except for a few KB of new fat which I seem to be stuck with.

Have just logged in susing Unity2 (only option available) and it is the view is the same..... I've also viewed it using "high contrast" in "universal Access" which would show any field that might be hidden by the format.... Nada....

I had version 5.0.6 installed and Oneiric was listed as version 5.0.1.4 but even forcing downgrade to that made no difference..... Although it does load much faster now..... There are several reports of search problems in Launchpad, just not my particular one.

Anyway Raj.... I think I will stick with Synaptic to search and terminal to install.... That way I have a full record of what has been installed/changed/removed which I am able to paste into Gedit.

Thank you for your help Raj.

I will mark this as solved.....

---

### Post by maureenc on 2012-05-07
Finally found the solution... by accident!

I had set my text size to be "large" in Universal Access..... For some reason this stops the input field from being displayed..... Can't see why as there is more than enough space for it!

Who would have thought that would have such an effect?

---

