---
title: "Need Older but recent versions of Flash"
date: 2011-12-09
forum: General Help
---

### Post by Amurko on 2011-12-09
I'm using the Flash-Aid plugin for Firefox to get the latest flash (also tried the repositories) but the latest Flash they insist on using (both 32-bit and 64-bit) are unsatisfactory.

I *need* to use an older version of flash from a few months ago that worked fine.  Can anyone provide links to the older versions?  A .tar.gz should work fine.

---

### Post by oldtimer7777 on 2011-12-09
> **Amurko said:**
> I'm using the Flash-Aid plugin for Firefox to get the latest flash (also tried the repositories) but the latest Flash they insist on using (both 32-bit and 64-bit) are unsatisfactory.

I *need* to use an older version of flash from a few months ago that worked fine.  Can anyone provide links to the older versions?  A .tar.gz should work fine.

Try Flash Aid plugin for Firefox. Change the script generator to use the "Stable" version, and you should have what you are looking for...

---

### Post by BBQdave on 2011-12-09
> **Amurko said:**
> I'm using the Flash-Aid plugin for Firefox to get the latest flash (also tried the repositories) but the latest Flash they insist on using (both 32-bit and 64-bit) are unsatisfactory.

I *need* to use an older version of flash from a few months ago that worked fine.  Can anyone provide links to the older versions?  A .tar.gz should work fine.

Unsure difference between *old flash* and *latest flash*, other than bug and vulnerability fixes.

For safe surfing, I would use *latest flash* :)

---

### Post by Amurko on 2011-12-09
> **BBQdave said:**
> Unsure difference between *old flash* and *latest flash*, other than bug and vulnerability fixes.

For safe surfing, I would use *latest flash* :)

What good is the latest flash if it won't even load the videos?  I don't care if the older one has vulnerabilities; if it loads the video, it's fine!

Btw, I've just reinstalled my system and the latest flash won't load videos maybe 80% of the time..  both before AND after reinstall!

---

### Post by sammiev on 2011-12-09
I used [this]("http://ubuntuforums.org/showthread.php?t=1358591&page=41&highlight=flash") method on 3 computers over the last 3 or so weeks and all working great. Read post 403.

---

### Post by oldtimer7777 on 2011-12-09
The one it is using is the older one you are asking for.. Shiesh..   You want to try the beta version with the script generator?  Try it. Download it directly from Adobe and install it with Flash Aid.  Flash Aid will install any version you download manually.  Do you know how to use it right?

Do a simple search on Google Search Engine for any named flash installation compressed file that contains whatever version you want..   Uncompress it, point Flash Aid Plugin to that *.so flash plugin file and you are done. 

> **Amurko said:**
> ATQ (or ATFQ)!!!!  Don't ask why.

(ATQ = Answer the Question!)



Did you read my message?  I AM using Flash Aid.



What good is the latest flash if it won't even load the videos?  I don't care if the older one has vulnerabilities; if it loads the video, it's fine!

Btw, I've just reinstalled my system and the latest flash won't load videos maybe 80% of the time..  both before AND after reinstall!

---

### Post by lovinglinux on 2011-12-14
> **oldtimer7777 said:**
> The one it is using is the older one you are asking for.. Shiesh..   You want to try the beta version with the script generator?  Try it. Download it directly from Adobe and install it with Flash Aid.  Flash Aid will install any version you download manually.  Do you know how to use it right?

Do a simple search on Google Search Engine for any named flash installation compressed file that contains whatever version you want..   Uncompress it, point Flash Aid Plugin to that *.so flash plugin file and you are done.

Actually, Flash-Aid can install from tar files, it doesn't install extracted *.so files.

Get the old version you want from [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Extract the zip file and locate the Linux tar.gz file inside it. Don't need to extract it. Open Flash-Aid Advanced Mode dialog from the extension menu, select "Custom" in the installation option menu, browse and select or type the path to the downloaded and extracted tar.gz file. Click the Script tab and click Execute button.

**Note:** there is a bug in the Custom install on the current version of Flash-Aid. I suggest you get version 2.2.2 from my site.

---

### Post by Amurko on 2011-12-18
> **lovinglinux said:**
> Actually, Flash-Aid can install from tar files, it doesn't install extracted *.so files.

Get the old version you want from [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Extract the zip file and locate the Linux tar.gz file inside it. Don't need to extract it. Open Flash-Aid Advanced Mode dialog from the extension menu, select "Custom" in the installation option menu, browse and select or type the path to the downloaded and extracted tar.gz file. Click the Script tab and click Execute button.

**Note:** there is a bug in the Custom install on the current version of Flash-Aid. I suggest you get version 2.2.2 from my site.

THANK You!  Finally got my flash working again after installing the custom Flash-Aid!  (Selected Adobe Stable from Repositories 64-bit, not sure why installing it from repositories in Synaptic or Ubuntu software center was a no go but hey it worked.) :D

---

### Post by lovinglinux on 2011-12-19
> **Amurko said:**
> THANK You!  Finally got my flash working again after installing the custom Flash-Aid!  (Selected Adobe Stable from Repositories 64-bit, not sure why installing it from repositories in Synaptic or Ubuntu software center was a no go but hey it worked.) :D

Because there is a bug with *flashplugin-installer* on 64bit systems. If you have the partner repository enabled, then Flash-Aid installs *adobe-flashplugin* instead, which is the real 64bit plugin and not the 32bit with the wrapper.

---

