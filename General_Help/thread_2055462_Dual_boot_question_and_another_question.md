---
title: "Dual boot question and another question"
date: 2012-09-09
forum: General Help
---

### Post by cstambaugh on 2012-09-09
Ok so I have a dual boot setup, mainly because I still need Windows 7 for some school programs and the teachers will not accept the open source alternates. 

I have Ubuntu 10.04, and when I do some updates, I have multiple entries on the startup screen for Generic linux and was wondering how to remove some of them. Before I re installed due to a hardware issue I had about 20 entries... how can I remove the unused ones?

Also, Whatis the easiest way to update flash and java on the Chrome browser? It keeps telling me it is out of date, but when I try to update the iced tea to version 7, it says it cannot be found. 
What are some other opinions for browsers on Ubuntu? I use Firefox for one desktop and Chrome for another desktop, did some searches but need some "coaxing" on what to choose to try...

Thanks 
Chris

---

### Post by sienile on 2012-09-09
```
sudo update-grub
``` should get rid of all the extra entries. You will still have 2 for your install (normal and recovery), the MemTest entries, and one for your Windows install.

As far as your browser problems, I use Chromium and I haven't had issues with the normal installers for either. It should act the same way as Chrome. Are you doing the default install or manually selecting the most recent version? Java works best on version 6 instead of 7.

---

### Post by cstambaugh on 2012-09-09
> **sienile said:**
> ```
sudo update-grub
``` should get rid of all the extra entries. You will still have 2 for your install (normal and recovery), the MemTest entries, and one for your Windows install.

As far as your browser problems, I use Chromium and I haven't had issues with the normal installers for either. It should act the same way as Chrome. Are you doing the default install or manually selecting the most recent version? Java works best on version 6 instead of 7.

Thanks for the reply,
I have tried the command line and the installer packages, even tried using the converter to convert the RPM to a deb and use the installer to do it. Still says plugin is out of date.

---

### Post by critin on 2012-09-09
This will help fix the extras on grub page.

[http://ubuntuforums.org/showthread.php?t=1664134&highlight=boot+customizer](http://ubuntuforums.org/showthread.php?t=1664134&highlight=boot+customizer)

> 
 the easiest way to update flash and java on the Chrome browserWhen chrome says its out of date, doesn't it give the option to let it update?  check it's Tool icon and see what you can find.

You can update through synaptic package manager I believe.  Just click Status, then Installed Upgradeable, find chrome/chromium in the list and click update/upgrade.

---

### Post by cstambaugh on 2012-09-09
> **critin said:**
> This will help fix the extras on grub page.

[http://ubuntuforums.org/showthread.php?t=1664134&highlight=boot+customizer](http://ubuntuforums.org/showthread.php?t=1664134&highlight=boot+customizer)



When chrome says its out of date, doesn't it give the option to let it update?  check it's Tool icon and see what you can find.

You can update through synaptic package manager I believe.

It does and it takes me to the page to download the RPM files but they dont install right using the terminal commands it gives me.
Currently I am on Version 6 of the Iced Tea plugin, and It wont let me update to number 7. Tells me it cant find the update. Everytime I open a chatroom I frequent, it tells me the plugin is out of date. I was considering maybe a different browser, maybe Maxthon or something not sure...

---

### Post by critin on 2012-09-09
> **cstambaugh said:**
> It does and it takes me to the page to download the RPM files but they dont install right using the terminal commands it gives me.
Currently I am on Version 6 of the Iced Tea plugin, and It wont let me update to number 7. Tells me it cant find the update. Everytime I open a chatroom I frequent, it tells me the plugin is out of date. I was considering maybe a different browser, maybe Maxthon or something not sure...

I won't push this any more, but have you gone to Synaptic package manager and checked for updates?

Click on Status and then in the list that comes up in the left window, click Installed (upgradeable). then "mark all upgrades" and install.

Or you can reinstall a new one from Software Center, or choose another browser.  It probably needs more upgrading than just Iced Tea, so while you're at it just do it all.

---

