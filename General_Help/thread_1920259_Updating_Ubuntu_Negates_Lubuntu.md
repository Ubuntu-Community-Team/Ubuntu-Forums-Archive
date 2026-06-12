---
title: "Updating Ubuntu Negates Lubuntu?"
date: 2012-02-04
forum: General Help
---

### Post by Th1rt3enXIII on 2012-02-04
I installed Lubuntu on an old refurbished laptop, and after the initial installation, the update manager said that there was an update for Ubuntu that could be applied. Thinking that this would only update what was on my system and not install new packages, I let the machine update. Now, my system runs at twice as much memory as before I updated Ubuntu.

I am guessing that it was a stupid mistake on my part, since the update seemed to install all of the packages that do not come with Lubuntu in the first place. Now, I would like to revert back to the original Lubuntu installation and start over without reinstalling the and losing everything. I'm basically wanting to rollback the latest Ubuntu update. I know this is probably a stupid question to all of you, but I'm still learning.

What would be the best route to take besides a complete reinstall?

---

### Post by Th1rt3enXIII on 2012-02-04
Also, I would like to know if I am correct in assuming that updating to the newest version of Ubuntu would negate the Lubuntu installation.

---

### Post by SteveDee on 2012-02-04
> **Th1rt3enXIII said:**
> ...What would be the best route to take besides a complete reinstall?

You could try this: [http://psychocats.net/ubuntu/purelxde](http://psychocats.net/ubuntu/purelxde)

Just select the correct version based upon the version you have currently.

In a terminal type:-
```

lsb_release -a

```

Note that you will get "Ubuntu" even with Lubuntu installed, but it will tell you the version number.

---

### Post by SteveDee on 2012-02-04
> **Th1rt3enXIII said:**
> Also, I would like to know if I am correct in assuming that updating to the newest version of Ubuntu would negate the Lubuntu installation.

Usually, upgrading from Lubuntu should give you a newer version of Lubuntu. Not sure how you ended up with Ubuntu, but I may be missing the point.

---

### Post by Th1rt3enXIII on 2012-02-04
After installing Lubuntu, it notified me that there was a Ubuntu update available. I began thinking that the Ubuntu update installed all of the packages that are left out in the Lubuntu installation. If I am incorrect about this, please let me know. That would mean that I am attempting to fix the wrong issue. I just know that my memory usage was a lot lower before the Ubuntu update.

---

### Post by Th1rt3enXIII on 2012-02-04
SteveDee, that link provided me with just what I was looking for. I was unable to remove all extra Ubuntu packages that were installed with the latest update, and now my memory usage is back to normal.

Thanks a lot for the help!

---

### Post by LinuxFan999 on 2012-02-04
> **Th1rt3enXIII said:**
> I installed Lubuntu on an old refurbished laptop, and after the initial installation, the update manager said that there was an update for Ubuntu that could be applied. Thinking that this would only update what was on my system and not install new packages, I let the machine update. Now, my system runs at twice as much memory as before I updated Ubuntu.

I am guessing that it was a stupid mistake on my part, since the update seemed to install all of the packages that do not come with Lubuntu in the first place. Now, I would like to revert back to the original Lubuntu installation and start over without reinstalling the and losing everything. I'm basically wanting to rollback the latest Ubuntu update. I know this is probably a stupid question to all of you, but I'm still learning.

What would be the best route to take besides a complete reinstall?
Which version of lubuntu did you install?

---

