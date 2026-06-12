---
title: "Drivers/Programs questions...."
date: 2009-07-16
forum: General Help
---

### Post by TF2-Engi on 2009-07-16
I got ubuntu running, now to get my drivers going, unless I don't need them...which I probably need them.  Ok I have an XFX GTX 260 Core 216, with a drivers disk, but I am guessing it only works with windows, so where can I get Ubuntu drivers for it?  Also I heard a lot about Wine and Cedega, there are a select few games that I want to play on linux.  I mainly want to play TF2 which I read plays great on it?  Also I want to play other source games like half life 2 and the expansions and maybe portal.  Which "Emulator" (Yes I know Wine Is Not an Emulator) should I use?  Could I use both?  Thank you!

---

### Post by starcraft.man on 2009-07-16
1. Gfx drivers, System > Admin > Hardware drivers > Select card and install. Then you need to either restart or just log off and on, resets the session.

2. WINE is free, Cedega is a paid for version. Cedega is really just WINE with a nice front end GUI and some extra tweaks they make to increase computability.

You can install wine from the respositories, use the following command in the terminal:

```
sudo apt-get install wine
```

To get tf2 working, you'll need to install Steam. Download it from the web, then use WINE on it. [FAQ is here.]("http://wiki.winehq.org/FAQ") After that, you should be able to download or install tf2 from backup. I know I got steam working before, so I'm pretty sure you shouldn't have trouble. If you want more info on installation, see sig.

---

### Post by TF2-Engi on 2009-07-17
> **starcraft.man said:**
> 1. Gfx drivers, System > Admin > Hardware drivers > Select card and install. Then you need to either restart or just log off and on, resets the session.

2. WINE is free, Cedega is a paid for version. Cedega is really just WINE with a nice front end GUI and some extra tweaks they make to increase computability.

You can install wine from the respositories, use the following command in the terminal:

```
sudo apt-get install wine
```To get tf2 working, you'll need to install Steam. Download it from the web, then use WINE on it. [FAQ is here.]("http://wiki.winehq.org/FAQ") After that, you should be able to download or install tf2 from backup. I know I got steam working before, so I'm pretty sure you shouldn't have trouble. If you want more info on installation, see sig.

OK everything seems to be working pretty well.  Thank you!!!!  Is play on linux any good?

---

