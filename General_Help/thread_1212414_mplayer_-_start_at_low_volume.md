---
title: "mplayer - start at low volume?"
date: 2009-07-13
forum: General Help
---

### Post by Cephi on 2009-07-13
i thought this would be easy... i read the man, i put in some quality time with google, and i tried many things myself, but i can't figure out how to start mplayer at less than full volume.  any help would be appreciated.

---

### Post by chriskin on 2009-07-13
you can always use other frontends of mplayer, like gnome-mplayer and smplayer

gnome-mplayer keeps your last settings, or at least it does for me.

---

### Post by Cephi on 2009-07-13
i only use mplayer from cli
plus it's a matter of principle at this point -- this should be easy, and i bet it probably is, i just can't figure out how to do it.

---

### Post by Vaphell on 2009-07-13
i played a little and it should do the trick
mplayer -af volume=<some number> <filename>

0 appears to be default volume level, negative numbers make sound quiet.

---

### Post by rvm4000 on 2009-07-13
With newer versions of mplayer, you can also use the -volume option:

mplayer -volume 50 <filename>

The range for the -volume option is 0-100.

You can of course add a line like this in ~/.mplayer/config to start mplayer always with the same volume:
```
volume=50
```

PPA with a recent mplayer version:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by Cephi on 2009-08-10
> **rvm4000 said:**
> With newer versions of mplayer, you can also use the -volume option:

mplayer -volume 50 <filename>

The range for the -volume option is 0-100.

You can of course add a line like this in ~/.mplayer/config to start mplayer always with the same volume:
```
volume=50
```

PPA with a recent mplayer version:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

Am I missing something?  I've got the newest version of mplayer, but it doesn't recognize the -volume option.  Adding volume=50 to my config has no effect either.

---

### Post by zkriesse on 2009-08-10
There should be a default option in the mplayer menu...let me download it and get back to you man...

---

### Post by andrew.46 on 2009-08-10
Hi Cephi,

> **Cephi said:**
> Am I missing something?  I've got the newest version of mplayer, but it doesn't recognize the -volume option.  Adding volume=50 to my config has no effect either.

The newest version of MPlayer looks like this:

```
andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n1[/COLOR]**
MPlayer SVN-r29481-4.2.4 (C) 2000-2009 MPlayer Team
```

If you are using rc2 rather than an svn build perhaps this option is a later addition?

Andrew

---

### Post by rvm4000 on 2009-08-10
> **Cephi said:**
> Am I missing something?  I've got the newest version of mplayer, but it doesn't recognize the -volume option.  Adding volume=50 to my config has no effect either.

If you have installed mplayer 1.0rc2, that's not the newest version of mplayer, actually it's a very old version.

The -volume option was added to mplayer in svn r27872 (2008-10-31). Get a package from here and you'll have the -volume option: [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by Cephi on 2009-08-10
Ah lovely, that did it.  Thanks!

---

