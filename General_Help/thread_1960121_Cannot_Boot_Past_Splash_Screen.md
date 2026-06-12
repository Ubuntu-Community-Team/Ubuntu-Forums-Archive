---
title: "Cannot Boot Past Splash Screen"
date: 2012-04-16
forum: General Help
---

### Post by electrojustin on 2012-04-16
Ok I'm stumped. I recently reinstalled xubuntu (package issues, no idea) and have found that, after reinstalling and updating my software, I now freeze on the xubuntu splash screen. I've tried recovery mode, reinstalling lightdm, reinstalling xubuntu-desktop, reinstalling xubuntu-default-settings, and even reinstalling the whole thing,  but nothing seems to work. At the moment I'm on a livecd chrooting into my / partition. I'm trying to get command line access to the machine without the need of the livecd and I might try an older kernel, but I'm starting to run out of ideas. Anything you can offer, please do so. Thanks in advance for any suggestions.

---

### Post by bogan on 2012-04-17
Hi!, **electrojustin**, Do you get a grub menu ? [If necessary press shift key]

If so, select your Ubuntu entry, press 'e' to edit the script, navigate to the Linux boot line and replace 'ro quiet splash', with 'ro --verbose text', press 'Ctrl+X' to boot to a text login prompt.

The text display should give you some clues as to what is wrong, or where it is hanging.

```
sudo service gdm start 
```will show if the graphics are working. [ I am not sure if 11.04 still uses gdm, if it does not run, try 'lightdm' instead of 'gdm' in the code].

Chao!, **bogan.**

---

