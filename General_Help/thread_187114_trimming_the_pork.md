---
title: "trimming the pork"
date: 2006-06-02
forum: General Help
---

### Post by xinix on 2006-06-02
What do you uninstall to trim the fat off your system?  I'd like to slim my system down as much as possible.  Some applications I can easily recognize as something that I won't use/need.  There are a ton of packages I don't recognize  but might just end up sitting there as harddrive fillers.

Thanks.

---

### Post by blackjack6.21.91 on 2006-06-02
Just use synaptic to look at installed packages (status --> installed) and if your **absolutely** sure you don't need them, then you can go ahead and mark them for complete removal.  Most applications will probably depend on ubuntu-desktop.  It's ok to remove that package.  It really doesn't mean very much.  It shouldnt break your system or anything.

---

### Post by jecos on 2006-06-02
You can open up synaptic and look in Status section and remove all the local/obsolete packages.  Then run "sudo apt-get autoclean" "sudo apt-get clean"

---

### Post by magnusbb on 2006-06-02
If you don't need all the fonts for other languages the yours, you can trim off 100MB, and it makes the  X server at bit snappier also, I think - as you don't have to load all the fonts you never use.

---

### Post by dralaroc on 2006-06-02
Great question I just removed all the bluez stuff, hp printer stuff, gaim, rsync, and some other stuff.  I kinda was wondering about the fonts.  Oh I also removed that raid thingy ;)

---

### Post by davegod75 on 2006-06-02
how do i remove the extra fonts(foreign)? i.e. what are the package names

---

### Post by xinix on 2006-06-02
Wow, I didn't realize how many language fonts are installed.

---

### Post by dralaroc on 2006-06-02
I looked for stuff like this when I typed "fonts" in the synaptic search box.  Especially the foreign language ones.

---

### Post by Skye on 2006-06-02
Some of these have already been mentioned, but upon a new install, I remove:
-Foreign fonts
-Bluetooth (bluez)
-HP Linux and Printing (hplip* and hpijs)
-Evolution
-Old kernels (but make sure you don't remove the current kernel)
-Ekiga softphone
-Handicapped compatibility (gnopernicus, gtk2-engines-highcontrast)
-Modem dialing software (ppp, pppconfig, pppdcapiplugin, ppp-dev, pppoe, pppoeconf, pppstatus, wvdial)

I've also installed something called localepurge (sudo apt-get install localepurge) which removes locales you don't want.

---

### Post by dralaroc on 2006-06-02
Aaah...thanks skye for your list.  I forgot about ekiga,high contrast & ppp stuff.  Yeah, I do the same thing on a clean install also ...localespurge & gtkorphan its part of my routine now.

---

### Post by cleentrax on 2006-06-02
This is all good advice, but be sure to keep a live CD around in case someone who needs another language, or high-contrast themes, would like to use your computer.

---

