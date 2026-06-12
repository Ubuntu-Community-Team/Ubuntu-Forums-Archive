---
title: "Wine re-install problem"
date: 2006-04-29
forum: General Help
---

### Post by richardward101 on 2006-04-29
I've messed up my wine, and I need to know how to reset it back to as it would be with a default installation. I tried using synaptec to completely remove, and deleting ~/.wine but that just made the reinstall unable to find or create hard disks for wine. I'd rather not use winetools if possible as that seems to be what messed wine up in the first place.
Thanks for any advice

---

### Post by hollywoodb on 2006-04-29
Do NOT use winetools.  That probably did mess up wine in the 1st place.

```

sudo apt-get --purge remove wine
rm -rf ~/.wine
sudo apt-get install wine

```
that should cleanly reinstall wine for you

to rebuild ~/.wine/ and such, the 1st thing you should do once wine is installed is

```

winecfg

```

also, use [http://www.winehq.com/site/download-deb]("http://www.winehq.com/site/download-deb") for up to date wine packages.  if you're not using that, follow these steps instead:

```

sudo apt-get --purge remove wine
rm -rf ~/.wine

<start up synaptic and follow the steps to enable wine repositories as in above link>

sudo apt-get update  (if you get errors about wine repos, see note below)
sudo apt-get install wine
winecfg

```

NOTE: if you get errors about wine repositories, edit /etc/apt/sources.list by hand and make sure the two wine lines read:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by richardward101 on 2006-05-01
Could have sworn thats what i tried before, but following your instructions it worked. Thanks!

---

