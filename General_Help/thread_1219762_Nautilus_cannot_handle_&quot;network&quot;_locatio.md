---
title: "Nautilus cannot handle &quot;network&quot; locations."
date: 2009-07-22
forum: General Help
---

### Post by g0nad on 2009-07-22
I'm using Ubuntu Alternate 9.04 with WindowMaker, I've installed nautilus for the purpose of browsing SMB/windows shares but when I click on nautilus' network icon I get the message "Nautilus cannot handle "network" locations.".

I believe that I'm probably missing a package but whatever package I'm missing wasn't a dependency of nautilus.

If I install KDE's "dolphin", that can browse network shares. I don't like dolphin, I'd rather have nautilus work as it does in a default Ubuntu install.

I'm stuck, has anyone been able to solve this before?

---

### Post by Vaphell on 2009-07-22
[http://ubuntuforums.org/archive/index.php/t-186127.html](http://ubuntuforums.org/archive/index.php/t-186127.html)

supposedly package libgnomevfs2-extra should do the trick

---

### Post by g0nad on 2009-07-23
Thanks for the help but I'm afraid that's not it.  I've got the following packages installed:

  libgnomevfs2-extra
  smbfs

---

### Post by g0nad on 2009-07-23
I'm probably going to hold out another 37.26 hours then give up and just install stock "Ubuntu" then change my window manger to WindowMaker and just live with the excess cruft that Canonical have decided to inflict on everyone.

---

### Post by g0nad on 2009-07-24
Well, I persevered kept 'Ubuntu Alternate'.  I installed gnome-desktop-environment so that nautilus was working in the environment it wanted.  I then began to remove packages until nautilus broke, once I'd isolated which package had a negative impact I stopped and only installed that package.

It was 'gdm'.  (I was surprised too)

So now I login using GDM into Window Maker and when I run nautilus the network folder behaves as I expected.

I think it's because gdm allows nautilus to hook into a bunch of gvfs stuff in a way that it wants.

---

### Post by g0nad on 2009-07-24
I did some more trial and error and found that launching my window manager using dbus-launch seems to let nautilus do the right thing (I've purged gdm).

So my .xinitrc now contains:
```

conky &
dbus-launch --exit-with-session wmaker
```

---

