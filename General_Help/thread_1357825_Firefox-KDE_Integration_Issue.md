---
title: "Firefox-KDE Integration Issue"
date: 2009-12-17
forum: General Help
---

### Post by James78 on 2009-12-17
Note: For more people to understand the nature of this issue, there is a hack that OpenSUSE has developed for KDE, to make Firefox use KDE default dialogs, folder choosing, etc. There is an Ubuntu PPA for this already. You can find more information at [http://en.opensuse.org/KDE/FirefoxIntegration](http://en.opensuse.org/KDE/FirefoxIntegration)

Problem: Firefox is not using the KDE folder choosing dialogs, etc, it is using the default and drabby Gnome dialogs, when it should be using the KDE ones!!! The first time I installed this, it worked great! However, over the course of some upgrade to the packages or something, it stopped working. I've uninstalled, reinstalled, purged, deleted every single file and reinstalled, I've tried every trick in the book related to installing and uninstalling. I have not been able to get this functionality back.. =( Any ideas?

Related packages installed:
xulrunner-1.9.1-kde
xulrunner-1.9.1 (hacked for KDE)
kmozillahelper
firefox-3.5
And all Gnome firefox counterparts are also installed.

Background information:
Firefox 3.5.6
Kubuntu 9.10 Karmic Koala
Ubuntu firefox-kde PPA - [ppa:debfx/firefox-kde]("https://launchpad.net/~debfx/+archive/firefox-kde")
Any more needed info? Just request it...

---

### Post by James78 on 2009-12-18
Bumpp.

---

### Post by treris on 2009-12-18
I had it working very nicely up until the update to FF 3.5.6, haven't been able to get it working again after that, even with reinstalling it....

PS there's more on this here: [http://ubuntuforums.org/showthread.php?p=8521730#post8521730](http://ubuntuforums.org/showthread.php?p=8521730#post8521730)

---

### Post by lovinglinux on 2009-12-18
I tried, but it didn't worked well, so I removed the ppa repository and firefox, then installed it again. Now, all my confirmation dialogs have the Cancel button on the right and the OK button on the left, just like Firefox Windows, which is pretty annoying.

Is not a profile issue, since this happens on all, profiles. Anyone knows how to revert this?

EDIT: I have found an workaround, but is not the ideal. It consists of adding the following line to userChrome.css

```
.dialog-button-box { -moz-box-direction: reverse; }
```

Does anyone knows where that version of firefox saved this dialog hack so I can remove it?

---

### Post by lovinglinux on 2009-12-18
> **lovinglinux said:**
> I tried, but it didn't worked well, so I removed the ppa repository and firefox, then installed it again. Now, all my confirmation dialogs have the Cancel button on the right and the OK button on the left, just like Firefox Windows, which is pretty annoying.

Is not a profile issue, since this happens on all, profiles. Anyone knows how to revert this?

EDIT: I have found an workaround, but is not the ideal. It consists of adding the following line to userChrome.css

```
.dialog-button-box { -moz-box-direction: reverse; }
```

Does anyone knows where that version of firefox saved this dialog hack so I can remove it?

Nevermind. I was able to revert the changes by re-installing xulrunner

---

### Post by Kyril on 2009-12-19
KMozillaHelper 0.6.0 should be ready soon.

edit: Don´t work for me! :(

---

### Post by treris on 2009-12-19
The XUL runner update fixed things for me!

---

### Post by James78 on 2009-12-20
Kk, thanks guys, I didn't think it was me since everything seemingly failed after the update for some reason.

Edit: Looks like there's an update for this, might work after. =)
Edit2: Yup, the update fixed it. I'll remember that the packages must need to be updated to fix this next time this happens.

---

