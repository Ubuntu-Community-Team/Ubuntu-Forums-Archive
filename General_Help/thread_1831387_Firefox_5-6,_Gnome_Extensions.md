---
title: "Firefox 5-6, Gnome Extensions"
date: 2011-08-23
forum: General Help
---

### Post by RylosFan on 2011-08-23
Hoping "General Help" is the best place for this, apologies if not.

I've been installing the latest, stable FF releases manually.

I'm running Lucid, I've **_not _**added the Firefox stable PPA (*mozillateam/firefox-stable*), long since removed 3.6, and I'm stuck on finding the Gnome integration that came along with 3.6.  

For instance, attempting to "open containing folder" I'm unable to set Firefox to simply open a downloaded file's location with Nautilus.  Attempting to configure within "Applications" results in the Nautilus trying to open the file rather than simply open a window.  So, either I'm making some serious noob mistake (more likely) or there's something missing from my install.

I've poured over [THIS ]("http://ubuntuforums.org/showthread.php?t=1712247&highlight=gnome+extensions+firefox")thread, I couldn't find anything relevant to my situation.

Can anyone confirm the Gnome extensions for Firefox 4 and up in Lucid?   I realize the repo would alleviate having to sudo FF for updates but everything I've looked into seems to have been tailored for 3.6 and is not compatible with subsequent releases.  Is there something I've missed?

Thanks!

---

### Post by raja.genupula on 2011-08-23
you mean opening your folder with firefox . i am working fine with firefox 7 . if this what you want , i can provide you what you want

---

### Post by RylosFan on 2011-08-23
From the screenshot, that's not exactly what I was looking for.  

From within Firefox, I used to be able to view the "Downloads" dialogue window, right-click on a file, and select "Open Containing Folder", a Nautilus window was then launched in the "Downloads" directory showing all files I had saved.

Now, I probably should have gone on to state this impacts other functionality such as MPlayer running inside FF rather than separate window.

---

### Post by raja.genupula on 2011-08-23
```
sudo dpkg-reconfigure firefox
```
close the firefox while trying this

---

### Post by RylosFan on 2011-08-23
I'll give it a shot, thanks!

---

### Post by raja.genupula on 2011-08-23
you're welcome . let me know what you got . if you got it . please dont forget to mark as solved  the thread , from thread tools

---

### Post by RylosFan on 2011-08-24
I'm getting: "firefox is broken or not fully installed".

---

### Post by raja.genupula on 2011-08-24
yeah thats saying we have errors in the firefox . so better to go for reinstall the firefox . other wise do one thing , do upgrade of firefox . 

[http://www.webupd8.org/2011/05/install-firefox-nightly-from-ubuntu-ppa.html](http://www.webupd8.org/2011/05/install-firefox-nightly-from-ubuntu-ppa.html)

---

### Post by RylosFan on 2011-08-30
Sorry for the extremely delayed response, I'll have to try an install from the repo.

---

### Post by RylosFan on 2011-10-21
Thank you for your help, Raja.  I know this is a seriously late response, I just had a chance to get back to this machine last night.  Adding the repo and re-installing did the trick! 

I does bother me a bit I couldn't find any documentation on installing/configuring these extensions myself; seems kinda like nuking an ant hill by re-installing Firefox but hey, it does the trick.

---

