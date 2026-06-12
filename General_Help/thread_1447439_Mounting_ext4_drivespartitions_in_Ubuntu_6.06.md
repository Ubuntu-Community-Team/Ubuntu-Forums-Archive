---
title: "Mounting ext4 drives/partitions in Ubuntu 6.06"
date: 2010-04-05
forum: General Help
---

### Post by rosstripi on 2010-04-05
I just recently found an iso for 6.06 and installed it on an old pc of mine that already had 8.04 and crunchbang on it.  crunchbang is on an ext4 formatted partition.

When I setup 6.06, it asked me what i wanted to mount my drives as, so i told it to mount the ext4 system as hda1.

whenever 6.06 boots, it tries to mount hda1 but can't because it doesn't recognize ext4.

What I am asking is this: is there a deb or a package out there I can install to make 6.06 recognize ext4?  if not, how can i make it so that 6.06 does not want to mount hda1?

I can get past the initial error message and into the desktop, so 6.06 does work.

---

### Post by KeyserSoze93 on 2010-04-05
Not sure what you can do about that. Perhaps you could temporarily add some new repositories to your sources list, and install the metapackage for the kernel.

I have avoided using ext4 for this reason. Just out of interest, why are you trying to run 6.06?

---

### Post by djoxyk on 2010-04-05
Even my 8.04 does not recognize ext4. I had the same question when created installation for lucid while having hardy on another partition. I had to use ext3 for lucid due to compatibility issues.
Anyway, check [this]("https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Compatibility")
they say \Ext4 was released as a functionally complete and stable filesystem in Linux 2.6.28\

---

### Post by rosstripi on 2010-04-05
I'll try that, but I have a tendancy to cause the System Update to go haywire when I manually add repositories.

Well, it's an older computer (circa 2003).  Crunchbang runs the best out of all the operating systems I have tried.  My initial installation of Ubuntu 8.04 worked great... up until I installed a few programs.

I figured it was just eating up my RAM, so I wanted to try something that didn't use a desktop environment (crunchbang) or something that had an older desktop environment that probably wouldn't eat up so many resources (6.06).

---

### Post by rosstripi on 2010-04-05
I think I'm just going to edit /etc/fstab and make it so that it doesn't try to mount the partition at all.

---

### Post by KeyserSoze93 on 2010-04-15
> **rosstripi said:**
> I'll try that, but I have a tendancy to cause the System Update to go haywire when I manually add repositories.

Well, it's an older computer (circa 2003).  Crunchbang runs the best out of all the operating systems I have tried.  My initial installation of Ubuntu 8.04 worked great... up until I installed a few programs.

I figured it was just eating up my RAM, so I wanted to try something that didn't use a desktop environment (crunchbang) or something that had an older desktop environment that probably wouldn't eat up so many resources (6.06).

Well, I wouldn't switch to 6.06. 6.06 still uses GNOME, so it's still comparatively resource-heavy.

I'm running 8.04 with ext3 and [Fluxbox]("http://en.wikipedia.org/wiki/Fluxbox") window manager. You can install Fluxbox just by typing:

```
sudo aptitude install fluxbox
```

And then select it as your Session on the Log In screen. I think Crunchbang uses Fluxbox or something similar, but if you already have a working system installed, then it is simpler to just pop Fluxbox on as well. My PC and laptop run great with Fluxbox, despite their relative age.

This is really nice and lightweight, and it means I still have the advantage of relatively new versions of packages. Newer versions than 8.04 seem a bit slow of my hardware, however, so I have not upgraded further than that.

8.04 is Long Term Support, however, so all majors fixes are backported.

---

