---
title: "How to revert to standard xorg packages?"
date: 2009-07-24
forum: General Help
---

### Post by Richardcavell on 2009-07-24
Hi, all.

In an attempt to adopt the latest intel video drivers, I installed all of the packages from the xorg-edgy PPA.  Now my X won't boot at all. #-oI do have a backup but since I'm going to be doing some experimenting, I'd like to know if there's an elegant way to downgrade.

(By the way, I installed linux 2.6.30.  Do I need to wait for 2.6.31?  I'm using an Intel GMA 950, and the performance and compatibility under Jaunty is abysmal. However, people have claimed that the latest 2.8.0 versions of the Intel drivers fix a lot of problems.)

Anyway, I can at least get to a root shell.  Is there a command that I can use to un-upgrade those packages?  Something like force-install ubuntu-desktop would be nice - something that checks all packages against the current Jaunty stable versions and downgrades as appropriate?

Richard

---

### Post by philinux on 2009-07-24
If you can boot failsafe session from the login that would be a start. Or are you saying the gdm wont run.

---

### Post by Richardcavell on 2009-07-24
I sometimes get the startup sound, and I usually get a mouse pointer, but there is never any graphical display.

I can boot to a recovery mode, though, at my kernel selection screen, and get to a root shell.  From there I can use apt-get.  I just need to know what to type.

---

### Post by philinux on 2009-07-24
Not sure, I dont want to mess you up.

Have you tried xfix from the recovery menu?

---

### Post by Richardcavell on 2009-07-24
Yes, I have.  It doesn't work.  My xorg.conf doesn't have much in it usually anyway, so there's nothing much for it to fix.

Richard

---

### Post by philinux on 2009-07-24
Ok well from the shell you can use either cat or nano to look at what you installed.

cat /var/log/dpkg.log

You can use nano to edit your sources list to get rid of the ppa's and apt to uninstall the packages and the apt to install xorg from ubuntu.

---

