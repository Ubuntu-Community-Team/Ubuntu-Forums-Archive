---
title: "weird issue with ubuntu restricted extras"
date: 2009-08-01
forum: General Help
---

### Post by ffxigotenks on 2009-08-01
I've been helping a friend get an ubuntu box running, and whenever I install ubuntu-restricted-extras flash never works, we're both running 8.10 64 bit, I've tried everything to get flash working, I managed to do it before, but today I had to reinstall due to hardware issues, and flash is still not installing and I can't seem to make it work like I did before, help please:confused:

---

### Post by mikewhatever on 2009-08-01
Have you tried installing flashplugin-nonfree package separately?

---

### Post by Post Monkeh on 2009-08-01
> **ffxigotenks said:**
> I've been helping a friend get an ubuntu box running, and whenever I install ubuntu-restricted-extras flash never works, we're both running 8.10 64 bit, I've tried everything to get flash working, I managed to do it before, but today I had to reinstall due to hardware issues, and flash is still not installing and I can't seem to make it work like I did before, help please:confused:

be careful. i've found that if you have any more than 1 flash plugin installed it will stop flash working altogether.

---

### Post by ffxigotenks on 2009-08-01
I've tried uninstalling flashplugin-nonfree and gnash uninstalling whichever one I wasn't trying to use, gnash partially worked, insofar that the flash window would display, but the video would never load on youtube

---

### Post by XxionxX on 2009-08-01
I am having a similar problem with my flash. I can see adverts play and some flash graphics but I can't get youtube to work or play games. I have un-installed flash twice over the past two days trying to get it to work to no avail.

---

### Post by Raffles10 on 2009-08-01
The best way to get flash working in Ubuntu amd64 is to use the the 64bit flashplayer10 from adobe's website, the ones in the repo's just don't work:

Download flashplayer10 from adobe site: [flashplayer10]("http://labs.adobe.com/downloads/flashplayer10.html")

Extract 'libflashplayer.so' to ~/.mozilla/plugins, you may have to create .mozilla/plugins/ if it doesn't already exist.

Happy flashing. ):P

---

