---
title: "Installing Wine 1.3.32 in 9.10"
date: 2011-11-16
forum: General Help
---

### Post by tjscool914 on 2011-11-16
Hello, 

Im trying to install the latest developmental version of Wine (1.3.32) on a laptop running 9.10.  I've tried numerous times and it always installs Wine 1.3.15.  Does anyone know why I am unable to get version 1.3.32?  

Any help would be much appreciated!

Thanks

---

### Post by BillyBoa on 2011-11-16
If you go here

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

and click to the link _click this link to install the wine1.3 package._ you can install the last Wine version.

The problem is with 9.10 you are using I don't remember if the Software Center installs the .deb files or not.

Tell if it worked

---

### Post by tjscool914 on 2011-11-16
I went othe the winehg page and installed and added the repository through the software center and installed wine 1.3.  I also tried adding the repository manually and installing from command line.  Every time I uninstall and reinstall Wine1.3, from command line or through software center, it always installs Wine 1.3.15.  

I have another PC running 11.04 and had no issues installing Wine 1.3.32.  Are versions of Wine release dependent?

---

### Post by raja.genupula on 2011-11-16
> **tjscool914 said:**
> Hello, 

Im trying to install the latest developmental version of Wine (1.3.32) on a laptop running 9.10.  I've tried numerous times and it always installs Wine 1.3.15.  Does anyone know why I am unable to get version 1.3.32?  

Any help would be much appreciated!

Thanks

give a try by getting source of development version . for installation instruction read readme.txt file.

---

### Post by snowpine on 2011-11-16
> **tjscool914 said:**
> Are versions of Wine release dependent?

Yes, Wine does not waste their time and manpower developing for "end of life" Ubuntu releases.

It's probably time to upgrade to 10.04 or newer...

---

### Post by tjscool914 on 2011-11-16
OK I will try downloading from source.  I'm thinking this might be a version issue.  I would love to be at the current version of Ubuntu, but this laptop won't have any part of that.  Its a very old laptop that would best serve as a paper weight.  I tried installing 11.04 from a bootable flash drive but it wouldn't install properly.  I also tried upgrading to 10.04 once I installed 9.10.  Upon reboot it never came back... so I'm stuck at 9.10! 

Just wondering if its possible to get Wine 1.3.32 installed on 9.10 or if I must be on a more current version of Ubuntu.

Thanks

---

