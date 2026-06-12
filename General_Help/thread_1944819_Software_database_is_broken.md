---
title: "Software database is broken"
date: 2012-03-21
forum: General Help
---

### Post by cuberts on 2012-03-21
Hi,
I recently felt like getting Japanese on my ubuntu machine, so I just did went to System>Administration>Language Support and tried to install the language from there. 
However, the following error occurred when I tried to: 


Software database is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


I tried the command sudo apt-get install -f, and I need to upgrade about 1300 things. Yes, I haven't upgraded my ubuntu system in forever, I'm still running maverick. Still, I don't understand why this shouldnt work. Also, since it said it is impossible to install or remove ANY software, I just went to the Ubuntu software center and I was still able to install a bunch of random crap games and C++ Ide's, etc. So what is the issue here, how can I solve it? thanks in advance.

cuberts

---

### Post by cuberts on 2012-03-24
.

---

### Post by imachavel on 2012-03-24
I don't know I have never tried to install a language pack in ubuntu. In windows 7 it's a pain, you go install it through the control panel somehow, after downloading it, and you must go to a properties section and make sure the language is changed for each and every place the operating system reads the language settings, embedded in browser, for desktop, for reading menus, interface pop up, etc. And then it says it won't work unless you upgrade to windows 7 ultimate.

I'm only guessing ubuntu would have a similar language pack that would say it's selected for gnome or unity or kde, or if not have different settings for different places on the interface, embedded for the browser, etc. etc. for menu bar. I have never tried installing a language pack in ubuntu, but perhaps the package is unstable, have you googled for other packages, or googled for a package already in the software repository? Which can be accessed if you google how to find the ubuntu software center. There are literally thousands of apps for ubuntu. I'd try uninstalling the package with

sudo apt-get uninstall (package name)

that is... if you don't find the solution in this thread by tomorrow. And try a different language pack. Good luck

---

### Post by Bucky Ball on 2012-03-24
Try:

```
sudo apt-get update
sudo apt-get upgrade
```

... one at a time. This will update then upgrade packages, not the release.

---

### Post by imachavel on 2012-03-24
I thought sudo apt-get upgrade would update the release, if a new one was out. But yes sudo apt-get update will never hurt. What an awesome OS! So simple and yet so many features

---

### Post by Bucky Ball on 2012-03-24
> **imachavel said:**
> I thought sudo apt-get upgrade would update the release, if a new one was out. 

Nope, only packages, etc. 

ALWAYS run 'sudo apt-get update' before 'sudo apt-get upgrade', though. ;)

---

### Post by cuberts on 2012-03-27
Thanks for your replies, I get the same error message still, after I ran those commands.

---

### Post by QIII on 2012-03-27
This may be a regression.  I found a launchpad bug report from 2008.

One may use

```
sudo apt-get dist-upgrade
```

which does everything that upgrade does, but also attempts to resolve dependencies.

It does not upgrade to the next distribution, despite what many think.  That is a different command.

It may be worth a try, but it might not help.  The bug appears to be associated with adding localizations.

---

### Post by Narayana on 2012-07-08
I have tried all the things said here including update, upgrade.

Mine is a fresh installation of 12.04.  

(During install i noticed warnings to the effect that default locale file was not there.. if that was important)

I have since installed synaptic, gimp- their installation was smooth.

Problem is with installing language: 

When i tried to install language "telugu" in the language support,  it said "software database broken- you can not install or uninstall any package"  (Ofcourse i am able to install all packages other than the language packs!)

I desperately need a solution!! 

Experts, please suggest something...!!

Thanks.

---

### Post by Bucky Ball on 2012-07-08
I suggest starting a new thread outlining your issue and with a descriptive thread title. This one is old and has been asleep for awhile so you probably won't get much help here. ;)

---

