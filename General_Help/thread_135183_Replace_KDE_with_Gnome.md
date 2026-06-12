---
title: "Replace KDE with Gnome"
date: 2006-02-23
forum: General Help
---

### Post by cylent on 2006-02-23
Hello,

I installed Kubuntu today however i am not exactly very happy with KDE. Its been a while since i used linux so i figured why not use KDE. wrong. :mad: :mad: 

is it possible to download and run Gnome ? i'd hate to download Ubuntu fresh cause it'll take too long. 

it took me two nights to get Kubuntu install CD since i am on wireless.

---

### Post by aysiu on 2006-02-23
Open up a terminal (KMenu > System > Konsole) and type ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` It'll still take a long time to download but not as long as getting an entire CD's worth of stuff (close, though).

After that, log out. Pick Session > Gnome and log back in again.

Then go to Applications > Accessories > Terminal and follow [these directions to get rid of Kubuntu](http://www.ubuntuforums.org/showthread.php?t=96048)

Or... you could keep KDE, too, if you have the hard drive space for it (doesn't hurt).

---

### Post by cylent on 2006-02-23
thank you very much for the quick reply!

I will get right on this as soon as someone helps me fix my broadcom wifi adapter. :(

((Posted thread in Networking -- or search for posts in my name)) \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by Azzozhsn.NET on 2006-02-23
OK, how can I install KDE on Ubuntu?
I do not mean replace, I mean add it to my system.
thanks.

---

### Post by aysiu on 2006-02-23
[QUOTE=Azzozhsn.NET]OK, how can I install KDE on Ubuntu?
I do not mean replace, I mean add it to my system.
thanks.[/QUOTE] Same thing, except do ```
sudo apt-get install kubuntu-desktop
``` instead of ```
sudo apt-get install ubuntu-desktop
```

And if you want to uninstall Gnome, do [this](http://www.ubuntuforums.org/showthread.php?t=96046).

---

