---
title: "White blank icons in panel?"
date: 2010-05-01
forum: General Help
---

### Post by TheBadger on 2010-05-01
Have a look at my screenshot...

that is meant to be the battery icon and the email one, sometimes it does it to others and sometimes there are no white blocks but the battery logo will merge half and half with the email one..

something is wrong and I am stumped..


also a pretty much ubuntu newb so be kind please

help though my desktop looks rank!

[http://i41.tinypic.com/358p99f.jpg](http://i41.tinypic.com/358p99f.jpg)

---

### Post by WorMzy on 2010-05-01
Try this:

1) Goto: System -> Preferences -> Appearance
2) Click Customise
3) Choose a different set of controls

Does that make any difference at all?

If no:
1) Go to the Icons tab
2) Choose a different set of icons.

Does that make any difference?

---

### Post by TheBadger on 2010-05-02
nope thats not done anything sadly, still there with all the different icons and appearances.

any other ideas?

---

### Post by dino99 on 2010-05-02
sudo dpkg --configure -a

install gconf-cleaner and use it (yes to all)

---

### Post by TheBadger on 2010-05-02
that worked, thanks a lot!

---

