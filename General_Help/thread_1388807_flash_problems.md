---
title: "flash problems"
date: 2010-01-23
forum: General Help
---

### Post by timzorr on 2010-01-23
Im having some problems with flash in mozilla and chrome. video playback is fine but none of the buttons are working.for example i cant pause or change the volume. pretty sure my flash is up to date. i have ubuntu netbook remix on another pc without this same problem.:confused:

---

### Post by lovinglinux on 2010-01-23
If you are using 64bit, remove flash and install following [this tutorial](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by timzorr on 2010-01-24
When i disable desktop effects i find that the buttons work again. any ideas?

---

### Post by artmeacham on 2010-01-25
Exact same problem here.  I just noticed it within the last day or two, so it's probably caused by one of the recent updates.

While I'm sure the above solution works, I would prefer to stick with the repository version.  I want to avoid having to manually reinstall something as minor as the Flash plugin every time there is an update.  That's the joy of Ubuntu, right?

---

### Post by artmeacham on 2010-01-25
Confirmed that disabling desktop effects fixes the problem.  Compiz and Flash not playing well together?

---

### Post by HeadHunter00 on 2010-01-25
I know a better way to deal with this problem. Install mozilla gnash plugin (I am not sure about the actual name). Then install ubuntu-restricted-extras. I think thats what I did and firefox works like a charm now.

---

### Post by lovinglinux on 2010-01-25
> **HeadHunter00 said:**
> I know a better way to deal with this problem. Install mozilla gnash plugin (I am not sure about the actual name). Then install ubuntu-restricted-extras. I think thats what I did and firefox works like a charm now.

I don't think so. Gnash doesn't work on several web sites and installing restricted-extras after gnash will also install flashplugin-nonfree, which will result in plugin conflicts between the two.

---

### Post by HeadHunter00 on 2010-01-25
No, you just have to install extra codecs, and trust me, flashplugin-nonfree doesn't cause instability with gnash.

---

### Post by lovinglinux on 2010-01-25
> **HeadHunter00 said:**
> No, you just have to install extra codecs, and trust me, flashplugin-nonfree doesn't cause instability with gnash.

[Click here](http://www.google.com/search?q=lovinglinux+FOT004+site%3Aubuntuforums.org&) and look how many people had flash problems because gnash and flashplugin-nonfree were installed at the same time. The problem is not with flashplugin-nonfree, but with gnash that doesn't work for all sites and usually overrides flashplugin-nonfree. So the users install flashplugin-nonfree or restricted-extras but flash still doesn't work, because the browser uses gnash instead of flashplugin-nonfree.

What I recommend is to completely remove any flash plugin installed (swdec, gnash, adobe...), than install only flashplugin-nonfree.

If you are on 64bit, than use [this tutorial](http://ubuntuforums.org/showthread.php?t=1358591) instead.

---

