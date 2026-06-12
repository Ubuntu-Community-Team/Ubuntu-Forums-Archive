---
title: "flashplugin problem"
date: 2006-03-30
forum: General Help
---

### Post by pdobrev on 2006-03-30
Hello!
I noticed that after upgrading firefox, flash movies aren't working. However, I have the plugin installed and flash movies work in Mozilla.
I tried installing from the package from Macromedia website as well as the one in Dapper repositories. Both ways - no success. Running update-flashplugin results in:
installation failed.

If I run it with the downloaded plugin (i.e. locally) with update-flashplugin -l dir, I get
plugin changed, not trusted.

Anyone has an idea what may be the cause?

Thanks,
Petar.

---

### Post by danielph on 2006-04-18
I had problems with this plugin in Dapper. The install in Firefox failed (as usual) and the manual install failed as the server could not be found. Then went to Synaptic and installed from here. This all looked good, but didn't work. 

The answer was to download the tar and install manually from

[http://macromedia.mplug.org/](http://macromedia.mplug.org/) 

(you need rpm/source)

Extract the files, open up terminal and run ./flashplayer-installer in the directory you placed the files.


This worked for me.

Good Luck

---

### Post by pdobrev on 2006-04-19
Hi!

Thanks for your reply. Somehow that didn't work for me either but some time ago I found another solution, namely, to download a version of firefox for linux from the official firefox site. Then everything is ok with the flashplayer.

Petar.

---

