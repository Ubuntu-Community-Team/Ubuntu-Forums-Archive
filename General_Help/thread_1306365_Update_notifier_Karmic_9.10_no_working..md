---
title: "Update notifier Karmic 9.10 no working."
date: 2009-10-30
forum: General Help
---

### Post by stchman on 2009-10-30
Hello all.

I did a fresh install of Karmic x64 and all went smooth.  I was wondering if the little update notification will pop up a bubble telling you of available updates?  

The package update-notifier is installed.  I checked last night and there were (3) updates that needed to be installed and no popup.

Thanks.

---

### Post by Giblet5 on 2009-10-30
The update-notifier no longer hounds users about updates.

It's a feature. Search for "updates" in [this article]("https://wiki.ubuntu.com/NotifyOSD#Update").

---

### Post by stchman on 2009-10-30
I can understand the rationale, but a little popup is not that bothersome.  Oh well.

---

### Post by grandtoubab on 2009-10-30
gconftool -s --type bool /apps/update-notifier/auto_launch false

Applications -> System Tools -> Configuration 

it is the package gnome-system-tools 2.28

refer to 
[http://ubuntuforums.org/showthread.php?t=1128450](http://ubuntuforums.org/showthread.php?t=1128450)

---

