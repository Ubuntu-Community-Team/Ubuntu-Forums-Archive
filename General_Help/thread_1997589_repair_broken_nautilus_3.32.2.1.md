---
title: "repair broken nautilus 3.32.2.1 ??"
date: 2012-06-05
forum: General Help
---

### Post by mapuwenyi on 2012-06-05
I am using Ubuntu 11.4 with Gnome 2.32.1 and nautilus 3.32.2.1. Every once in a while nautilus seems to tag some folders as "taboo" in the sense that whenever I try to open them, the whole window closes down.

Restarting the computer is of no help, the same folder remains taboo. However, after a couple of days, the problem may disappear spontaneously, so it is not 100% reproducible, just some 90%. I still can have a look at taboo folders by using a terminal window or the midnight commander, and those folders and their files seem to be quite ok. Thus, I assume that Nautilus is broken or infected or simply buggy, but I do not know how to repair it.

Does somebody know how to remedy the above problem?

---

### Post by hakermania on 2012-06-05
So.... do all these folders share something in common?

---

### Post by dino99 on 2012-06-05
sudo dpkg-reconfigure nautilus

and think to watch ~/.xsession-errors & /var/log/ to find helpfull warnings/errors

---

### Post by mapuwenyi on 2012-06-05
@hakermania: I wish I knew!
The only common property I can think of is that they are folders which I have been using and reorganizing shortly before they became taboo. I might have renamed a folder or have shifted it to another place with some file in it left open or so. But I would not know how to tabooize a folder, it suddenly becomes "unopenable" and keeps being so.

---

### Post by hakermania on 2012-06-05
> **mapuwenyi said:**
> @hakermania: I wish I knew!
The only common property I can think of is that they are folders which I have been using and reorganizing shortly before they became taboo. I might have renamed a folder or have shifted it to another place with some file in it left open or so. But I would not know how to tabooize a folder, it suddenly becomes "unopenable" and keeps being so.

anything 'weird' to their name? Any possible weird character on the files inside?
How many files do these folders have inside?

---

### Post by mapuwenyi on 2012-06-05
:) PROBLEM SOLVED - THANK YOU :)

The name of the presently taboo folder was "svg_basictests" (without the quotes). But it must have included some invisible character, since renaming it to this very same name removed the impediment.

---

### Post by hakermania on 2012-06-05
> **mapuwenyi said:**
> :) PROBLEM SOLVED - THANK YOU :)

The name of the presently taboo folder was "svg_basictests" (without the quotes). But it must have included some invisible character, since renaming it to this very same name removed the impediment.

Nice :) I quite suspected that it was something like this!

Don't forget to mark this thread as solved :)

---

