---
title: "Google Chrome install on Debian - updating"
date: 2010-11-30
forum: General Help
---

### Post by mirakus on 2010-11-30
Hi.  I recently install Chrome on my Debian Lenny system, by downloading the .deb file from Google and using dpkg -i packagename as root.  I did notice that the page mentioned automatic updating, and noticed that installing the package added a google-chrome script to my /etc/cron.daily directory.  

I didn't know exactly how that was supposed to work, so I also went ahead and added Google's deb repository to my sources.list, that way I could upgrade it "normally."  Was this redundant/stupid?  How is the script in cron.daily supposed to work?  Can I leave it as is or should I remove the sources.list entry?  

Thanks for any help you can offer!

---

### Post by Brandon Williams on 2010-12-01
The cron job should have created a sources list for you under /etc/apt/sources.list.d/. On my machine, the file is called google-chrome.list and it contains:```
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
```

Provided that this file is present on your machine, too, then there is no need for you to have an addition config for this in your /etc/apt/sources.list file. If you search for google-chrome-stable in aptitude, does it show up under "Installed Packages" or "Obsolete and Locally Created Packages"? If it's under "Installed Packages", then you'll get updates when they're available.

---

### Post by mirakus on 2010-12-02
Hi Brandon.  

Thanks!  The google-chrome.list file was indeed created.  I wasn't aware that the sources.list could be augmented by other files like that, but I've only been using Debian-ish systems with apt for the past couple of years.  

Also, I don't use aptitude, but I can use 'apt-cache show' to show the package info after deleting the original deb, so all seems to be well.  

Thanks for clearing this up!  :D

---

