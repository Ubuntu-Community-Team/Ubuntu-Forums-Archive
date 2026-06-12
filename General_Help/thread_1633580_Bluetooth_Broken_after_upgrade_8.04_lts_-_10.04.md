---
title: "Bluetooth Broken after upgrade 8.04 lts - 10.04"
date: 2010-11-29
forum: General Help
---

### Post by njloch on 2010-11-29
Like so many others, after upgrading 8.04->10.04 LTS, Bluetooth is now busted.  I've spent the better part of a day trying to find answers; I've tried many things and the results have not been consistent.  I'm not going to write a book here as there are many other posts on the same problem and no real answers other than to complete a fresh install.  I CAN do that but I'll have to overcome one bothersome problem:

Bluetooth is an important protocol.  Now my (Bluetooth) broadband adapter is busted and I have to try and resolve this issue using a lousy phone line and modem.  Needless to say... I can't download a new distro with that configuration.  The updates would take weeks!

I suppose I'll have to drive into town and get someone to burn me a copy of 10.04 lts... Hope that works!

I'll think twice (or more) before upgrading an LTS distro again!  That machine was working great....I don't know why I upgraded.. security concerns mainly. live and learn I guess... live and learn....

If someone has a fix.. I'm all ears.. I can't afford the gas to drive into town for a few days yet...

---

### Post by tredegar on 2010-11-29
"Upgrades" do not go well in my experience.
Fresh installs do.

So when I moved from 8.04 to 10.04, I copied *all* my home files, to an external, **ext3** formatted, HDD (or just create a new partition for your new **/home** so you can keep your old home).

Do a fresh install.
Tweak it to your liking (BT & wireless working etc).
Apply all the updates.
Restore your files from the backup of **/home**

It worked for me.

Edit:
Meanwhile you can boot from your old 8.04 CD and download 10.04.1 using that if you are not ready for a drive into town yet.
/Edit

---

