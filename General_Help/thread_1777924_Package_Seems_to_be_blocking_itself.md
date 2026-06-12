---
title: "Package Seems to be blocking itself?"
date: 2011-06-08
forum: General Help
---

### Post by GodfreyPeck on 2011-06-08
I'm trying to install libbz2-dev on my labtop.
I'm running Kubuntu 10.04

jeff@jeff-laptop:~/Downloads/bzip2-1.0.5$ sudo apt-get install libbz2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libbz2-dev: Depends: libbz2-1.0 (= 1.0.5-4) but 1.0.5-4ubuntu0.1 is to be installed
E: Broken packages

When I tried to install it in Kpackagekit I got and error that says: A package dependency could not be found.
More information is available in the detailed report.
Details: The following packages block the installation: libbz2-dev (which is what I'm trying to install)


jeff@jeff-laptop:~/Downloads/bzip2-1.0.5$ sudo apt-get remove libbz2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libbz2-dev is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I'm trying to get PCSX2 going, and this is required; if that is relevant.
Anyone have any advice?

---

### Post by gmargo on 2011-06-08
The most likely reason is that your system is simply not up to date.  
Be sure to do an "apt-get update" and "apt-get upgrade", reboot if needed, and try your installation again.

---

### Post by Zorael on 2011-06-08
As gmargo says, make sure to update package lists first.

Also I suggest you use [**aptitude**](apt://aptitude) instead of apt-get. When faced with dependency issues aptitude will offer you solutions that resolve them, whereas apt-get will simply throw a fit and exit. apt-get is a mite faster though so I use it to update package lists, and then aptitude for the rest.

```
$ sudo apt-get update
$ sudo aptitude install libbz2-dev
```

---

### Post by GodfreyPeck on 2011-06-08
Thank you. 
I think I was fully updated (Though I've been getting some 404 sites not found during the update process), aptitude downgraded a couple things and then it ran fine.

---

