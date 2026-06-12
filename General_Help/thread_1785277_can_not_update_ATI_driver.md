---
title: "can not update ATI driver"
date: 2011-06-18
forum: General Help
---

### Post by enjoyubt on 2011-06-18
When i am in Hardware--Additional Drivers and wanna install ATI driver, but i got following prompt :
 
[COLOR=navy]W:Failed to fetch [/COLOR][[COLOR=navy]http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease")[COLOR=navy]  
, W:Failed to fetch [/COLOR][[COLOR=navy]http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease")[COLOR=navy]  
, W:Failed to fetch [/COLOR][[COLOR=navy]http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease[/COLOR]]("http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease")[COLOR=navy]  
, W:Failed to fetch [/COLOR][[COLOR=navy]http://extras.ubuntu.com/ubuntu/dists/natty/InRelease[/COLOR]]("http://extras.ubuntu.com/ubuntu/dists/natty/InRelease")[COLOR=navy]  
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]
 
My IE and Firefox work fine, so internet connection should be OK! 
 
Why do I get the error prompt ? Pls help!

---

### Post by christopher.wortman on 2011-06-18
In all my cases of Gentoo, Fedora, and all the *buntus, the latest ati driver is best installed by the .run package you get from the ati.amd.com website. The newest update patches a really big issue with the new Radeon HD X5k series' card bios. If you are one of the unlucky X5xxx owners and even in a few rare cases of x4xxx cases Linux cannot read the bios properly to tell Linux to upgrade the driver. Remember to uninstall the old one first. Then use the one from AMD's website. The fix will be out shortly, but in the meen time...

EDIT:You might be able to uninstall the old driver first and use the one from the repository as it is the latest version. Just uninstall the old radeon driver.

---

### Post by wildmanne39 on 2011-06-18
> **enjoyubt said:**
> When i am in Hardware--Additional Drivers and wanna install ATI driver, but i got following prompt :
 
[COLOR=navy]W:Failed to fetch [/COLOR][[COLOR=navy]http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease")[COLOR=navy]  
, W:Failed to fetch [/COLOR][[COLOR=navy]http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease")[COLOR=navy]  
, W:Failed to fetch [/COLOR][[COLOR=navy]http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease[/COLOR]]("http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease")[COLOR=navy]  
, W:Failed to fetch [/COLOR][[COLOR=navy]http://extras.ubuntu.com/ubuntu/dists/natty/InRelease[/COLOR]]("http://extras.ubuntu.com/ubuntu/dists/natty/InRelease")[COLOR=navy]  
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]
 
My IE and Firefox work fine, so internet connection should be OK! 
 
Why do I get the error prompt ? Pls help!Hi, here is a guide to get your driver installed properly.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)
and as for your updates they are not on the server or the server is down.

---

