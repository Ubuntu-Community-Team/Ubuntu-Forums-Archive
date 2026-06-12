---
title: "How to easily solve the Wi-Fi Broadcom-driver problem in 11.04"
date: 2011-04-28
forum: General Help
---

### Post by draKi91 on 2011-04-28
Hey guys,

As you might have noticed the new broadcom driver in 11.04 is not working anymore, but you can use the old one from 10.10 if you follow these steps:


**1. First you need to download the old broadcom driver (10.10) here:**

[http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

[B]
2. Now it's time to delete the current driver:[/B]

open the console:


sudo gedit /var/lib/dpkg/status


search for "bcmwl-kernel-source" and delete the lines that are related to the driver.
[B]
3. Install the driver you have downloaded before by double-clicking the .deb file
[/B]

[B]4. Go to the Synpatic-Package-Manager and search for "bcmwl-kernel-source" again.
  Click on on it and go to "package" and make sure you lock it, so it won't be updated.[/B]



Good luck!

---

### Post by postOSX on 2011-04-29
thank you, that was the ticket

---

### Post by AlanR8 on 2011-04-29
Broadcom driver worked out the box for me since about Alpha 3.

---

### Post by Technoviking on 2011-04-29
My Broadcom is working fine OOTB. Which NIC do you have? Also did you file a bug report on LaunchPad?

T-V

---

### Post by linuxswords on 2011-05-16
thx!!! you brought me back to the net ;)

---

### Post by ghoracek on 2011-08-04
> **draKi91 said:**
> Hey guys,



[B]4. Go to the Synpatic-Package-Manager and search for "bcmwl-kernel-source" again.
  Click on on it and go to "package" and make sure you lock it, so it won't be updated.[/B]



Both Ubuntu and Mint 11.04 versions 'break' my ability to wirelessly connect with my Dell Inspiron and I've been fighting this for months -- constantly uninstalling the latest version to go back to a version that works, then having an upgrade kill me again.  Tonight I'm going back to 10.04 (or maybe 9.04) to get wireless going again, but then I will try locking to prevent changes.  The older releases allow for selecting from two Broadcom drivers, the latest version only allows for using Broadcom STA which does not work with my Dell adapter -- no matter how hard I try to make it work. I'll report back

---

