---
title: "Firefox hangs"
date: 2010-07-06
forum: General Help
---

### Post by amiad.salton on 2010-07-06
I'm using Ububtu 9.04 and Firefox 3. From some point last week I haven't been able to open Firefox. When I try to open it, Firefox window is displayed and it hangs forever. It is not possible to do anything with Firefox window except killing it. 
I tried to reinstall it by Synaptic (Complete Removal) without success.
 
Any idea?

---

### Post by UberStudent on 2010-07-06
Try going to /home/yourusername/.mozilla/firefox and delete everything you see in that folder, then restarting Ff. This should make Ff like a new install.

---

### Post by amiad.salton on 2010-07-06
It solved the problem. Thank you very much!

---

### Post by lovinglinux on 2010-07-07
> **UberStudent said:**
> Try going to /home/yourusername/.mozilla/firefox and delete everything you see in that folder, then restarting Ff. This should make Ff like a new install.

When you recommend that, please make sure to inform the user he will lose all settings, passwords, extensions, bookmarks and so on.

I don't like to recommend profile deletion. IMO, is better to recommend creating a new profile to see if works, then copying the necessary files from the old profile.

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by UberStudent on 2010-07-15
I stated "This should make Ff like a new install", but I suppose that could stand spelling out.

---

### Post by lovinglinux on 2010-07-15
> **UberStudent said:**
> I stated "This should make Ff like a new install", but I suppose that could stand spelling out.

A new install is not the same as clean profile, since you can completely remove firefox, install it again and still have all your bookmarks, passwords and so on. Anyway, I'm bothering you because lots of people copy instructions and commands from other posts and lots of people recommend deleting the Firefox profile without even considering the user might have something important inside it.

---

### Post by clausfse on 2010-11-15
I have the same error, nearly daily. It cann't be a solution to erase the profile every day. Did you find out the reason for this strange behavior (frozen window)?

I use Ubuntu 10.10 and 9.10 (different machines) and Firefox  3.6.10

Thanks 

Claus

---

### Post by lovinglinux on 2010-11-15
> **clausfse said:**
> I have the same error, nearly daily. It cann't be a solution to erase the profile every day. Did you find out the reason for this strange behavior (frozen window)?

I use Ubuntu 10.10 and 9.10 (different machines) and Firefox  3.6.10

Thanks 

Claus

Try [https://addons.mozilla.org/en-US/firefox/addon/213326/](https://addons.mozilla.org/en-US/firefox/addon/213326/)

---

