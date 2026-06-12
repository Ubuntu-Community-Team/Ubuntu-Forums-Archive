---
title: "Downgrading Firefox"
date: 2011-04-01
forum: General Help
---

### Post by MrGrey1 on 2011-04-01
Lots of info on how to upgrade... now how to downgrade?
I don't like Firefox 4. Don't like having to install extra add-ons to restore basic functionality such as the status bar and lock icons. Please don't bother posting if you want to tell me how great v4 is or how I can 'fix' v4, I do not want to support this version so I will not use it... I want my old Firefox back.

So I uninstalled Firefox 4 and did an apt-get purge/clean/autoremove. Reinstalled firefox through synaptic and forced version 3.6.16.

Now when starting firefox I get 

"XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 31, Column 1:<window id="main-window"
^"

Firefox -profilemanager

XML Parsing Error: undefined entity
Location: chrome://mozapps/content/profile/profileSelection.xul
Line Number 53, Column 1:<dialog
^

I thought this might have something to do with the extra extensions I installed in 4 to get it working 'properly' so I went back to 4, uninstalled those extensions and tried again. Same errors. 

Any ideas?


EDIT: Removed v4 and then removed the repository as well. Reinstalled 3. Lost ALL my add-ons and old settings even though it's the same profile. Not happy! At least I have my status bar back.

---

### Post by tommcd on 2011-04-01
Have you tried renaming your ~/.mozilla directory to ~/.mozilla.bak? Then reinstall the FF that you want.
What version of Ubuntu are you using??
Ubuntu 10.10 only includes FF3.6.x.
If you are using Ubuntu 10.10, how did you install FF 4.0???

---

### Post by MrGrey1 on 2011-04-01
> **tommcd said:**
> Have you tried renaming your ~/.mozilla directory to ~/.mozilla.bak? Then reinstall the FF that you want.
What version of Ubuntu are you using??
Ubuntu 10.10 only includes FF3.6.x.
If you are using Ubuntu 10.10, how did you install FF 4.0???


I'm still on 10.4 actually... just added the repository and installed through synaptic.

3.6 is now working again... sort of. I can open my old profile and see all my bookmarks but all the add-ons are failing to load. They are in the add-on list and everyone of them says will be installed on restarting firefox but none of them install. I'm also now getting an add-on install pop-up with English GB/US and South African language packs popping up twice before FF will start... none of the packs actually install though. Going to go find a wall to beat my head against.

---

### Post by mastablasta on 2011-04-01
so basically you followed this guide: [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)
 
Yes in 10.04 it seems firefox 4 is not doing so well. not really sure why. But i lost the bookmarks and it seems to be the only thing that is missing. easy enough to fix though. while in 10.10 everything went fine and almost couldn't even notice it's a new version.
 
Something seems to have gone wrong in your case. easiest solution is to back up the bookmarks and such (as suggested) and simply reinstal the 3.6 from the repos. or you could give another try to FF4 :-) it's way more faster than 3.6.

---

### Post by Aracely on 2011-04-01
What version of Ubuntu are you using??
 
 
I don't use it....
 
 
 
 
 
 
 
 
 
___________________________________
[kindle](http://www.kindle-kindlecases.com/), [kindle cases](http://www.kindle-kindlecases.com/), [ps3 controller](http://www.egamebiz.com/ps3-controller-playstation3-controller.html), [xbox 360 controller](http://www.egamebiz.com/xbox-360-controller.html), [wii accessories](http://www.egamebiz.com/), [wii remote](http://www.egamebiz.com/wii-remotes.html)

---

### Post by ZaM0 on 2011-04-01
You can use ppa-purge:

```
sudo apt-get install ppa-purge && sudo ppa-purge ppa:mozillateam/firefox-stable
```

... or you can manually delete/disable the repository and reinstall any packages containing 'mfs' in their version name.

Then uninstall any addons upgraded for Firefox 4 and download their respective versions for Firefox 3.

---

### Post by dmbtimmyb212000 on 2011-04-02
> **ZaM0 said:**
> You can use ppa-purge:

```
sudo apt-get install ppa-purge && sudo ppa-purge ppa:mozillateam/firefox-stable
```

... or you can manually delete/disable the repository and reinstall any packages containing 'mfs' in their version name.

Then uninstall any addons upgraded for Firefox 4 and download their respective versions for Firefox 3.

Thanks a bunch for this tip.  Successfully reverted to 3.6.16, seems more stable @ this point with extensions fully operable.  :):guitar:

---

### Post by krtica on 2011-04-03
> **ZaM0 said:**
> You can use ppa-purge:

```
sudo apt-get install ppa-purge && sudo ppa-purge ppa:mozillateam/firefox-stable
```



Thank you, ZaMO, for the tip.
I use 10.04 x64.
I was unable to log in my bank account, right click menu was disappearing after moving mouse, auto-complete wasn't working in address bar etc.
Maybe it is faster and better, but there is something wrong with 4 in 10.04.

---

