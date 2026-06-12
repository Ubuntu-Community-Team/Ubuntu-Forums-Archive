---
title: "Adding Directories to AWN"
date: 2009-09-05
forum: General Help
---

### Post by Apex-jb on 2009-09-05
Anyone know how to add a directory to AWN? I can add launchers for apps but when I try to drag and drop a short cut to a directory, or a hard drive, it does not work. It will not let me manually add it either through the manager.

---

### Post by mc4man on 2009-09-05
It's actually not that difficult, for directories open up the awn manager -> launchers -> add.

You need to insert the command yourself, based on this

xdg-open /path/to/directory

Icons are a bit trickier, d. click on the icon space and wait for a pop up.

The location bar probably will default to home dir. If you wish to browse elsewhere expand the location bar and pick 'other' at the very bottom and browse from there.

Much easier to pick an icon first and copy to home folder, 48x48 hicolor png do well.

I don't use awn anymore but it's still installed on a tester, so quickly  added Music folder as shown in screen

Don't know what version you're using,  though when I did use it I found getting one from here better than the normal repo version

[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by Apex-jb on 2009-09-05
> **mc4man said:**
> It's actually not that difficult, for directories open up the awn manager -> launchers -> add.

You need to insert the command yourself, based on this

xdg-open /path/to/directory

Icons are a bit trickier, d. click on the icon space and wait for a pop up.

The location bar probably will default to home dir. If you wish to browse elsewhere expand the location bar and pick 'other' at the very bottom and browse from there.

Much easier to pick an icon first and copy to home folder, 48x48 hicolor png do well.

I don't use awn anymore but it's still installed on a tester, so quickly  added Music folder as shown in screen

Don't know what version you're using,  though when I did use it I found getting one from here better than the normal repo version

[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)
That worked. I didn't know you needed the xdg-open at the beginning.

---

