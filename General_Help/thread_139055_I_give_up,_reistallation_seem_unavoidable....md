---
title: "I give up, reistallation seem unavoidable..."
date: 2006-03-03
forum: General Help
---

### Post by ked on 2006-03-03
I never thought I had to go to this step....to reinstall ubuntu...

Unless someone has a bright idea of how to get my wireless, DVD/RW and sound devices work again. As posted earlier: my configuration is somehow changed (by a stupid installation script for some software I never got to work)  and I can't locate the corrupted files.

Isn't there a way to force Ubuntu to find the devices and reinstall them?

Totally lost,
Ked  :(

---

### Post by az on 2006-03-03
[QUOTE=ked]I never thought I had to go to this step....to reinstall ubuntu...

Unless someone has a bright idea of how to get my wireless, DVD/RW and sound devices work again. As posted earlier: my configuration is somehow changed (by a stupid installation script for some software I never got to work)  and I can't locate the corrupted files.

Isn't there a way to force Ubuntu to find the devices and reinstall them?

Totally lost,
Ked  :([/QUOTE]
sudo apt-get install --reinstall linux-image-`uname -r`


That will reinstall the drivers.  If you borked udev, you can try deleting the config and reinstalling udev.

---

### Post by ked on 2006-03-03
[QUOTE=azz]sudo apt-get install --reinstall linux-image-`uname -r`


That will reinstall the drivers.  If you borked udev, you can try deleting the config and reinstalling udev.[/QUOTE]


I've tried both without success. You would not believe all different stuff I've tried, all just a waist of time. I'm soon finnished reinstalling Ubuntu and will work the rest of the day configuring.

I'm quite dissapointed I never figured out what went wrong. Probably too easy to discover. Anyway, I will soon get a clean and smooth running installation.

Have a nice weekend
Ked

---

