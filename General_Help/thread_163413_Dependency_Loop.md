---
title: "Dependency Loop"
date: 2006-04-20
forum: General Help
---

### Post by Alev on 2006-04-20
Hello all.  A few moments ago I tried to get a gnome desklet for controlling xmms.  A quick google search turned up one called gxmms.
This isn't the main point of my request but I'm curious:  I tried getting it through synaptic.  All was fine an dandy, but when I tried to add it to the panel I got an error message: "The panel encountered a problem while loading "OAFIID:GNOME_gxmmsApplet"."  Anyone know what this means?  Anyways, I uninstalled through synaptic after that.

Now for the main part:
Google led me to the debian dot com repositories (if that's the right way to call them) and I tried getting the program through there.  I tried installing it with dpkg and I got a dependency error stating that gxmms-xmms needed the package gxmms-common.
So I get this new package, try to install it, and I get another dependency error: gxmms-common requires gxmms-xmms.
I checked syaptic and gxmms-xmms apeared as a broken package  so I deleted it from there.  I tried again a couple of times, with no success.

So what's the deal?  How can install one if it needs the other, and viceversa!  
I didn't put the exact messages I got because I've already closed the windows.  If they're important I'll redo the operation and put them up.

I get the feeling that the programmer for the package is getting a good laugh right now...

---

### Post by Qrk on 2006-04-20
Dependency errors can happen when you mix Debian and Ubuntu, so why don't we fix your first problem instead?

Try this:

```
sudo apt-get --reinstall install gnome-applets gnome-applets-data
```

Then:
```
sudo apt-get install gxmms
```

This should fix your first problem, but if it doesn't try doing this:

```
sudo apt-get remove gxmms
sudo apt-get install beep-media-player gxmms-bmp
```

---

### Post by zxee on 2006-04-20
This use to be know as dependency hell, and it's why package managers like apt or synaptic are popular. Some programs can be installed "by hand' but some are really tricky. I have xmms in my breezy install but don't have the gxmms applet.
If you need a frontend for a player what about xine and it's gui's? Hope that helps.

---

### Post by Alev on 2006-04-21
Thanks a lot the both of you.  I tried what you said Qrk, and it now works.
I thought that since Ubuntu is based on Debian, Debian packages worked fine with Ubuntu.  I guess this isn't completely true, but to what extent?  I'm curious, since Debian seems to have more recent versions of everything, so it seems handy.  Anyone know?  Anyways, thanks again for the help.

---

### Post by Qrk on 2006-04-22
[QUOTE=Alev]Thanks a lot the both of you.  I tried what you said Qrk, and it now works.
I thought that since Ubuntu is based on Debian, Debian packages worked fine with Ubuntu.  I guess this isn't completely true, but to what extent?  I'm curious, since Debian seems to have more recent versions of everything, so it seems handy.  Anyone know?  Anyways, thanks again for the help.[/QUOTE]

Most debian .deb files work on Ubuntu. But you shouldn't make a habit of mixing Debian and Ubuntu. Installing a couple of programs via .deb that you couldn't find in the repositories won't hurt anyone, but adding lines in /etc/apt/sources.list that refer to a Debian release is not a good idea.

---

### Post by Ramses de Norre on 2006-04-22
Because of the newer versions you can break a lot of stuff, when you install a newer program you'll may be needing newer libs, replacing the older ones needed for other ubuntu packages which can result in this ubuntu packages no longer working and so on.
So I'd stick to ubuntu when possible.
The reason why ubuntu has older versions is because the developers prefer older, well tested, stable software over bleeding edge, not as good tested and potential unstable software. The ubuntu packages are only upgraded between the releases for security reasons.

---

### Post by Alev on 2006-04-24
It's good to know.

---

### Post by adamkane on 2006-04-24
Remove the dotdeb line from your sources.list.

You can install some debian-specific packages on a case-by-case basis, but you should download these packages individually and install them with: 

```

sudo dpkg -i xxx.deb

```

If end up with a lot of deb files, you can put them in a folder and create your own repository with autorepo.

---

