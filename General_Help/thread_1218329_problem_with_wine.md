---
title: "problem with wine"
date: 2009-07-20
forum: General Help
---

### Post by nsblenin on 2009-07-20
I can run some windows aplications with wine. Some months ago I tried to run simcity4.exe and it worked well. Now I want to run it but every time I execute simcity4.exe with wine, it seems like it restarts X, that is to say it appears the welcome screen and I have to write the user and password.

Does someone know why it happens and how can I slove it? Thanks

---

### Post by LoneWolfJack on 2009-07-20
did you check appdb?

wine is a massive work in progress and regressions occur regularly so it's not uncommon for applications to stop working with later wine versions (they'll start working again with even later releases, though).

---

### Post by NightwishFan on 2009-07-20
Wine sometimes suffers from regressions. Did you configure Wine using the menu option to do so? Remember to autodetect disks as well.

If you want to try the newest Wine (I use the new one), I can link you a how to. Use this as a last resort, as it is beta software.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Edit: I checked wine appdb, and it gives Sim City between silver/platinum on different version, so things are hopeful. Do you have 3d drivers installed properly?

---

### Post by nsblenin on 2009-07-20
what is appdb?

Yes, I have drivers installed properly

---

### Post by xc1024 on 2009-07-20
AppDB is the database of all the programs ran on Wine and their users' reviews.
Go to winehq.org and in right top corner there is a search box. This is the place you type in the name of application you want to check (in your case probably Simcity 4).
On the loaded page you get the reviews of this app (SC4) and how well or bad does it work.
BTW, last time I checked SC4 had good reviews, so probably you have regressed Wine version. Wait a while for new version to come out, then try the game again after you update Wine. If it still doesn't work, try older versions.

Good luck.

---

