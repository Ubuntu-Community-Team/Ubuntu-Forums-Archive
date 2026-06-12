---
title: "Error #1 during Bulkr [AIR application] installation issue in Ubuntu 11.04"
date: 2011-06-07
forum: General Help
---

### Post by srsyrus on 2011-06-07
Hello !

I am a novice Ubuntu user. I recently installed Ubuntu 11.04 inside Win7 using Virtual Box. I have Ubuntu 10.04 as well.

In Ubuntu 11.04, as I try to install [Bulkr]("http://clipyourphotos.com/bulkr") [*An Adobe AIR application, bulk photo downloading tool for Flickr*], I keep getting an error dialogue box that says, "***The application could not be installed. Try installing it again. If the  problem persists, contact the application author. Error #1***". 

Please find the attached installation log file, where I noticed two unique errors :

[LIST=1]
[*][B]Error: Only root can install the application" 
[/B]
[*]**Error: dpkg: error processing /tmp/FlashTmp.HhLatV/setup.deb (--install)......................error in Version string 'v1.4': version number does not start with digit;**
[/LIST]
In Ubuntu 11.04, I am asked to input admin password during installation. I input the password but the installation ends with the error dialogue box. But in Ubuntu 10.04, I am not asked to input password & also had no issue installing & running the application.

Please suggest me on how can I get over this issue. Thanks in advance!

Regards,
Surya

---

### Post by mick222 on 2011-06-07
Adobeair might need it's permissions upgraded
```
chmod +x AdobeAIRInstaller.bin

```
This might help

---

### Post by srsyrus on 2011-06-07
> **mick222 said:**
> Adobeair might need it's permissions upgraded
```
chmod +x AdobeAIRInstaller.bin

```This might help

I tried installing with both the '.deb' & '.bin' installers. Adobe AIR installs fine. But the application Bulkr is not installing, ends with the same Error #1 dialogue box.:sad:

---

### Post by srsyrus on 2011-06-12
I am little sad to know that the forum is kinda passive! :( Or may be I posted my issue under the wrong section. 

Anyways, thanks a lot to Mick222 for looking out my issue. I guess, my question has been answered @[http://is.gd/OxwPS7]("http://askubuntu.com/questions/47805/error-in-version-string-v1-4-version-number-does-not-start-with-digit").

Regards,
Surya

---

### Post by linuxinstalledfromhdd on 2011-06-12
Did you change the permission of the installer file, and reinstall it yet?

---

### Post by Machiavelli on 2011-10-02
I'm having the same problem here. I did try to give the file (bulkr-v1.4.air) permission with no luck.

[http://clipyourphotos.com/bulkr](http://clipyourphotos.com/bulkr)

---

### Post by jerkfaceirl on 2012-02-02
Follow the comment here:

[http://askubuntu.com/questions/71760/error-version-number-does-not-start-with-digit](http://askubuntu.com/questions/71760/error-version-number-does-not-start-with-digit)

worked for me.

---

