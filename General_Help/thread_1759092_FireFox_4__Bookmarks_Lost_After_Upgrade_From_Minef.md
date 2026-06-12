---
title: "FireFox 4 : Bookmarks Lost After Upgrade From Minefield"
date: 2011-05-15
forum: General Help
---

### Post by ChipOManiac on 2011-05-15
It's stupid of me really... I had MineField on (FF4 Pre-Release) and went for a long time with it bookmarking and everything... Today I thought I'd upgrade to FF4... and assumed that the bookmarks would be kept...

And they weren't... boo...

So is there a special file or anything where the minefield bookmarks are kept?

Any help greatly appreciated...

---

### Post by n1ght5t4lk3r on 2011-05-15
not sure how the folder for minefield would be named but go to your home folder, show hidden files under the view menu and look in any folder related to mozilla (e.g.   .mozilla, .minefield etc) till you see a folder named something like xxxxxxxx.default which is your profile folder and bookmarks should be in there

---

### Post by lovinglinux on 2011-05-15
Minefiled profile folder is stored under ~/.mozilla/firefox-4.0/<profilename> while the default Firefox profile is stored under ~/.mozilla/firefox/<profilename>.

Close Firefox, make a backup of ~/.mozilla just in case, then copy the file places.sqlite from the minefield folder to the default folder.

---

### Post by ChipOManiac on 2011-05-16
Thanks A Lot Guys I Got The Bookmarks Back... Both Of You, Thanks A Lot :D Appreciate It...

---

### Post by lovinglinux on 2011-05-16
> **ChipOManiac said:**
> Thanks A Lot Guys I Got The Bookmarks Back... Both Of You, Thanks A Lot :D Appreciate It...

You are welcome.

---

