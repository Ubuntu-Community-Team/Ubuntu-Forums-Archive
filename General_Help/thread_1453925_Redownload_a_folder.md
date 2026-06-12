---
title: "Redownload a folder?"
date: 2010-04-13
forum: General Help
---

### Post by cdude42 on 2010-04-13
hey i need some help. i really screwed up the folder /usr/share/icons/ by tryin to manually replace cursors and stuff. so where can i redownload the entire folder? or what do i need to do to get it back to normal?

---

### Post by Tman5293 on 2010-04-13
Can you go into some more detail as to what exactly is wrong with the folder?

---

### Post by cdude42 on 2010-04-13
well theres nothing wrong with it, its just really messy. I have multiple cursor themes going at the same time and it bugs me.

---

### Post by Tman5293 on 2010-04-13
Well then the only thing you can do about it is try and clean it up your self. Try deleting some unused icon themes.

---

### Post by hryanjones on 2010-04-13
Another brute-force option if you still have your install cd is to just copy the folder from the running LiveCD.

To do this you'd have to follow these general steps:
[LIST=1]
[*]Boot up using the Live Disc (I'd imagine it's important to have the same version of Ubuntu that you've installed)
[*]Mount your primary partition (usually this is as simple as opening the appropriate "Hard Drive" icon in Nautilus (assuming that's your file manager)
[*]Delete everything in your messy folder (note that this folder will be at a location like /media/ActualUbuntuHD/usr/share/icons)
[*]Copy everything in /usr/share/icons (which should be the LiveCD version) to the now empty folder on your actual install HD
[/LIST]

Another idea is to go into Synaptic and remove packages that just appear to be icons and reinstall a few.  It seems gnome has a number of sets of icons like
*gnome-icon-theme*

Hope one of those works out for you.

---

