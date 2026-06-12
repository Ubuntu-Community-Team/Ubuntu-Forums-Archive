---
title: "Firefox makes hard drive go crazy"
date: 2011-06-06
forum: General Help
---

### Post by MartyBuntu on 2011-06-06
So I'm using 10.04 with Firefox 4 and when I run Firefox my hard drive thrashes like crazy. 

This doesn't happen at all if I use Chrome.
I've tried disabling all plug-ins/add ons...no differnece.
Cleared cache/regular maintenance...no go.

Why?

And gone through many iterations of Flash with FlashAid...not any better.

---

### Post by linuxinstalledfromhdd on 2011-06-06
Let's start by cleaning it out.

sudo apt-get install bleachbit

sudo bleachbit

(careful not to delete your passwords or bookmarks)

---

### Post by MartyBuntu on 2011-06-06
Do you mean I should uninstall Firefox?

---

### Post by LowSky on 2011-06-06
> **MartyBuntu said:**
> Do you mean I should uninstall Firefox?

Don't do that.

Firefox shouldn't be accessing your hard drive really at all. I have never seen that behavior

Best thing to do is make a backup of your bookmarks. Thengo to your home folder, make hidden files viewable (CTRL+H) find the .mozzilla folder and delete it.

Basically it will take Firefox back to a clean slate

---

### Post by MartyBuntu on 2011-06-06
Whoa...

Used Bleachbit to delete Browsing History and Vacuum...

It seems like that did it. Drive access isn't spazzing out any more.
Thanks everybody!

---

