---
title: "Upgrade or fresh install?"
date: 2011-04-29
forum: General Help
---

### Post by PCaddicted on 2011-04-29
When I switch to Natty,do you recommend upgrading or doing a fresh install?The latter is not desirable at all,since it would mean reinstalling all software...and,even worse,a new Ubuntu version is released every 6 months...

---

### Post by Lateralis on 2011-04-29
I've never had a problem upgrading from version to version, so I would personally do a distribution upgrade.  You will need to upgrade your system as far as possible before the dist upgrade, and I tend to close everything down and do nothing whilst it is upgrading.  

If you did want to install a fresh, I've just found the following commands may be of use to you:

```

sudo dpkg --get-selections > /path/to/savefile
sudo dpkg --set-selections < /path/to/savefile && sudo apt-get dselect-upgrade

```

The first creates a list of installed programs in the file that you specify, whilst the second reads in this file and attempts to install them.  If you have a separate /home partition then all of your personalisations are saved even if you do a fresh install.

---

### Post by Frogs Hair on 2011-04-29
I prefer a clean installation . I use some PPA/S and most of them become out dated with each new release . I backup home , make a list of applications I use not installed by default and I'm off to the races .

---

### Post by sg1efc on 2011-04-29
> **Lateralis said:**
> I've never had a problem upgrading from version to version, so I would personally do a distribution upgrade.  You will need to upgrade your system as far as possible before the dist upgrade, and I tend to close everything down and do nothing whilst it is upgrading. 

I have also not had any problems doing the upgrades.  While I always had to do complete reinstalls when I used to use Windows (had no choice with windows, every 6 months it seemed, Lmao), haven't had any problems myself with upgrading Ubuntu.  :)

If you do an upgrade, Lateralis' suggestions are definitely good to do.

---

