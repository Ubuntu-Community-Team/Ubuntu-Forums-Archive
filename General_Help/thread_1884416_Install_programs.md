---
title: "Install programs"
date: 2011-11-21
forum: General Help
---

### Post by meetdilip on 2011-11-21
hi, just got Ubuntu on my laptop. It has Firefox 3.6, so I downloaded latest FF from Mozilla site. But I don't see any option to install it. Anything I click gets extracted. Please tell me how to install software (not just FF).

Also need help here too

[http://ubuntuforums.org/showthread.php?t=1884413](http://ubuntuforums.org/showthread.php?t=1884413)

---

### Post by drmrgd on 2011-11-21
Unlike Windows, Ubuntu has a software download and installation tool (kind of like an app store, but free) for pretty much all the software you'll ever need.  This way you won't have to manually download software and run into the complicated process of installing, as you've already found out.  Plus all the software is monitored to be virus free and safe.

On the panel should be a link for the Ubuntu Software Center.  When you open it up, search for Firefox, and you should be able to download and install from there.

---

### Post by crazy bird on 2011-11-21
If you want the latest stable Firefox do this:
 
- open a terminal
- type in the commands: 
**sudo add-apt-repository ppa:mozillateam/firefox-stable**
**sudo apt-get update**
**sudo apt-get upgrade**
 
This way you will update your Firefox to the latest version.
 
 
A question from my side: which program's you want to update? 
 
@drmrgd:
By using Ubuntu Softwarecenter or Synaptic you won't get the latest versions of some program's, just updates without version changes. If you want the latest version, you have to check launchpad for it, or the website of the company that produces those software.

---

### Post by meetdilip on 2011-11-21
Thanks, updating Firefox through terminal. Please check the other thread too.

---

### Post by meetdilip on 2011-11-21
Also it does not show whether I have 64 bit or 32 bit OS. My laptop is  good in hardware, so would prefer 64 bit. If I upgrade, will I be asked  to select from 32 and 64 bit version ?

---

### Post by bryncoles on 2011-11-21
Hi meetdilip.  

Type ```
uname -a
``` into a terminal to see if you have the 64 bit version.  I think you're looking for something like "x86_64" to appear in the output (someone will correct me if I'm wrong).  

And I don't think upgrading will move you from 32 to 64 bit.  You'd have to reinstall I'm afraid.

---

### Post by mastablasta on 2011-11-21
appropriate one for your os should be installed.
 
basically this command adds sort of "personal" repository in adition to those found in software center.

---

### Post by meetdilip on 2011-11-21
Mine is 32 bit. :(

---

