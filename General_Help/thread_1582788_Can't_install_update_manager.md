---
title: "Can't install update manager"
date: 2010-09-27
forum: General Help
---

### Post by rafussen on 2010-09-27
I have been using Ubuntu for about 8 months now. For some reason (after having messed around with things) I no longer have Update Manager. I now want to easily upgrade to v. 10.04.1, but since I don't have Update Manager, I can't do it. So, I attempted to install it via Ubuntu Software Center, and upon downloading the software, this error comes up each time:

Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Futhermore [sic] there could be a conflict between software packages which are not allowed to be installed at the same time.

And then the only text of the "Details" is "update-manager." Upon attempting to install Update Manager via a terminal, the following is the result:

rafussen@rafussen-desktop:~$ update-manager
The program 'update-manager' is currently not installed.  You can install it by typing:
sudo apt-get install update-manager
update-manager: command not found
rafussen@rafussen-desktop:~$ sudo apt-get install update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  update-manager: Depends: update-manager-core (= 1:0.126.6) but 1:0.126.10 is to be installed
E: Broken packages

My guess is that last part is probably helpful, but my newbieness prevents me from deciphering anything. So, any help as to why I can't get Update Manager and how to remedy that would be helpful. Thanks.

---

### Post by jmszr on 2010-09-27
rafussen,

Here is a link to the update-manager-core package (1:0.126.6): [http://packages.ubuntu.com/karmic/update-manager-core](http://packages.ubuntu.com/karmic/update-manager-core)  

Edit: Here's a link to the update manager package (1:0.126.6): [http://packages.ubuntu.com/karmic/update-manager](http://packages.ubuntu.com/karmic/update-manager) . (Just in case that's of any use.)

Hope that helps.

---

### Post by rafussen on 2010-09-28
I'll be honest, I don't know what to do with those links. I don't know if/how to install anything on those package sites, if that is what I need to do. I guess I need instructions. I'm still learning.

---

### Post by andrewthomas on 2010-09-28
post the output of 

```
aptitude show update-manager-core
```

and ```
aptitude show update-manager
```

---

### Post by rafussen on 2010-09-29
rafussen@rafussen-desktop:~$ aptitude show update-manager-core
Package: update-manager-core
State: installed
Automatically installed: no
Version: 1:0.126.10
Priority: optional
Section: admin
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 5,194k
Depends: python (< 2.7), python (>= 2.5), python-central (>= 0.6.11), python2.6,
         python-apt (>= 0.7.5), lsb-release, python-gnupginterface
Recommends: libpam-modules (>= 1.0.1-9ubuntu3)
Conflicts: computer-janitor (<= 1.11-0ubuntu1), update-manager (< 1:0.93.7)
Replaces: update-manager (< 1:0.93.7)
Description: manage release upgrades
 This is the core of update-manager and the release upgrader

rafussen@rafussen-desktop:~$ aptitude show update-manager
Package: update-manager
State: not installed
Version: 1:0.126.6
Priority: optional
Section: gnome
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 1,642k
Depends: python (< 2.7), python (>= 2.5), python-central (>= 0.6.11), python2.6,
         gconf2 (>= 2.10.1-2), update-manager-core (= 1:0.126.6), synaptic (>=
         0.57.8), gksu, python-dbus, python-vte, python-gconf
Recommends: software-properties-gtk (>= 0.71.2)
Description: GNOME application that manages apt updates
 This is the GNOME apt update manager. It checks for updates and lets the user
 choose which to install.

---

### Post by rafussen on 2010-10-07
Any more replies/help?

---

### Post by andrewthomas on 2010-10-07
post the output of 
 
```
 
sudo apt-get install update-manager

```

---

### Post by caleb.g.lawson on 2010-10-07
If you can't get Update Manager installed the alternative would be to run this in the terminal:
```
sudo apt-get upgrade
```

You can usually go into Synaptic Package Manager and fix the broken packages that way, but I am at a loss at remembering how.

---

### Post by rafussen on 2010-10-09
Here are the two outputs, they were unsuccessful:

rafussen@rafussen-desktop:~$ sudo apt-get upgrade
[sudo] password for rafussen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




rafussen@rafussen-desktop:~$ sudo apt-get install update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  update-manager: Depends: update-manager-core (= 1:0.126.6) but 1:0.126.10 is to be installed
E: Broken packages
rafussen@rafussen-desktop:~$

---

### Post by rafussen on 2010-10-18
Anybody else able to help? Seems like a fix someone out there is capable of doing, but I clearly am not advanced enough to do it myself.

---

### Post by Pollox on 2010-10-19
Okay, since this has been sitting here for a week without activity, my idea:

The problem seems to be that update-manager depends (that is, it requires) an older version of update-manager-core than you have installed. How did this happen? Who knows? You probably enabled some third-party repo or downloaded a deb file of the newer update-manager core.

How to fix it: Let's use Synaptic. (Under System > Administration)
1) Go to Edit > Fix Broken Packages (might need to hit apply after that) See if that fixes it. If not, on to
2) Type update-manager-core in the search box. Select it, then go to the Package Menu, select Force Version, and choose version 1:0.126.6 from the drop down menu (again, click apply when you're done)

---

### Post by rafussen on 2010-10-20
Sweet, it worked! The second option (forcing version of update-manager-core) worked. Since there were no broken packages, the first option obviously was inapplicable.  Thank you so much.

---

### Post by lavinog on 2010-10-20
In the future you should do the following first:
```

sudo apt-get update

```

---

### Post by okkie on 2010-11-13
I am still having a similar problem and cannot understand how this one is marked SOLVED without being solved.

I am learning fast!

---

### Post by lavinog on 2010-11-13
> **okkie said:**
> I am still having a similar problem and cannot understand how this one is marked SOLVED without being solved.

I am learning fast!

If the similar problem is "dpkg broken/synaptic doesn't open"
Please stick to the thread you created.  Assuming that this thread is about the same issue will only lead to confusion and waste your time.

---

