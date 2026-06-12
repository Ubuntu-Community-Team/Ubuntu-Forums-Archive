---
title: "Miro opens containing folder instead of playing files"
date: 2011-05-23
forum: General Help
---

### Post by ben2talk on 2011-05-23
A problem I encountered after upgrading to Natty, which disappeared after doing a fresh install, has returned...

When I click 'play' in Miro, instead of opening my chosen preferred application (currently audacious) it doesn't play the files now - it opens the containing folder. 

Double clicking the file there opens the file as I want Miro to do...

Why is Miro doing this? gPodder works fine...

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did you add the repo and upgrade it yet?

[https://launchpad.net/~pcf/+archive/miro-releases](https://launchpad.net/~pcf/+archive/miro-releases)

---

### Post by ben2talk on 2011-05-24
Actually I think this isn't a Miro issue.

Downloads (jpg/torrent/pdf etc) from browsers also open with Nautilus.... however, clicking them in nautilus opens them according to the mime.

The same happens if I use a terminal and type 'gnome-open' or 'xdg-open'

e.g. gnome-open test.torrent
Expected - open with deluge
Actual - opens with Nautilus

---

### Post by linuxinstalledfromhdd on 2011-05-24
[http://ubuntu-tweak.com/source/miro/](http://ubuntu-tweak.com/source/miro/)

---

### Post by ben2talk on 2011-05-24
Ok, thanks - Miro is fine - it's the opening of files that's borked in a number of applications.

I suspect gnome-open and xdg-open just gave up on me.

---

### Post by linuxinstalledfromhdd on 2011-05-25
It may need updates through the PPA to fix those issues.  It's really your best best at this point.

---

### Post by ben2talk on 2011-05-25
[http://ppa.launchpad.net/pcf/miro-releases/ubuntu](http://ppa.launchpad.net/pcf/miro-releases/ubuntu) is in my sources list.

The best way to add it is to use **ppa: pcf/miro-releases**
The latest version available in the dropdown selector is 'Maverick' - and so I'm wondering if Miro may have caused issues with other applications...

Even if I don't launch Miro, Firefox and Chrome will replicate the issue.

---

### Post by ben2talk on 2011-06-27
> **linuxinstalledfromhdd said:**
> It may need updates through the PPA to fix those issues.  It's really your best best at this point.

This didn't work - files downloaded with Miro, Chromium and Firefox all do this - if I try to open or play a file, the containing folder is instead opened in Nautilus.

---

