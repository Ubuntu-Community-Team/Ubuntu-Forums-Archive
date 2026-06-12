---
title: "Something Odd with FireFox"
date: 2010-04-11
forum: General Help
---

### Post by MikeMarsh on 2010-04-11
My Firefox version is 3.5, Ubuntu 9.10.  As of yesterday, DNN 5.XX sites menus have ceased to render properly.  Opera, Epiphany, and all of the Windows browsers (including FireFox) render a nice compact menu bar.  The Ubuntu box expands and slams the menu to the left of the screen.

Tried reinstalling and cleaning out the configuration files.  No joy.  Any ideas?

Looked over the Firefox troubleshooting solutions not getting anything like this there.

Mike

---

### Post by NT4usB on 2010-04-12
By 'configuration files' do you mean you deleted or renamed your profile folder and created a new profile?
Are you running any add-ons?

---

### Post by MikeMarsh on 2010-04-14
> **NT4usB said:**
> By 'configuration files' do you mean you deleted or renamed your profile folder and created a new profile?
Are you running any add-ons?
deleted all the files in mozilla/firefox, reinstalled without addins.  Still getting the issue.  Contemplating stepping back a version.   This is probably something really simple.

---

### Post by gradinaruvasile on 2010-04-14
You mean your personal settings stored in 

/home/username/.mozilla/firefox/

folder? 


The easiest way to test the newest firefox is to remove the above folder, download firefox from their site, unpack it somewhere and run the firefox executable from that folder.

---

### Post by MikeMarsh on 2010-04-14
> **gradinaruvasile said:**
> You mean your personal settings stored in 

/home/username/.mozilla/firefox/

folder? 


The easiest way to test the newest firefox is to remove the above folder, download firefox from their site, unpack it somewhere and run the firefox executable from that folder.
Yes indeed.  Everything under .mozilla/firefox

---

### Post by MikeMarsh on 2010-04-16
Gave Synaptic "mark for complete removal" a spin and did a reinstall.  Still have the issue.

---

### Post by Aped on 2010-04-16
Switch to Google Chrome.


Edit: Seriously.

---

### Post by MikeMarsh on 2010-04-17
I test websites with multiple browsers.  This one is the odd-ball.

---

### Post by MikeMarsh on 2010-04-18
Tried something different.  Wubi on a deskop box that was over a month out of date.  Same issue persists there.

Guess I can stop with the install/uninstall/reinstalll pain loop.

10.04 comes out the 29th.  Wait isn't that how we fix Windows?

---

