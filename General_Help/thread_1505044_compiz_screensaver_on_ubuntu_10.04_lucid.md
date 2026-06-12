---
title: "compiz screensaver on ubuntu 10.04 lucid"
date: 2010-06-08
forum: General Help
---

### Post by moseba on 2010-06-08
hey
i want to install screensaver and some other plugins in compiz on ubuntu 10.04 lucid
can any one help me???

---

### Post by WorMzy on 2010-06-08
What do you mean? Compiz doesn't have a screensaver plugin (as far as I know of), and Ubuntu uses gnome-screensaver to render and control screensavers. If you want to install more screensavers, then take a look at this website: [http://gnome-look.org/index.php?xcontentmode=187](http://gnome-look.org/index.php?xcontentmode=187)

If you want all the compiz plugins, then run this in a terminal:```
sudo apt-get install compiz-plugins compiz-fusion-plugins-main compiz-fusion-plugins-extra
```

---

### Post by moseba on 2010-06-09
no and don't mean that
there is another plugins in compiz that i don't have on ubuntu 10.04 lucid
like:flying windows , freely tansformable windows and there is a plugin in compiz called screensaver
i remember i had these plugins in ubuntu hardy but i don't have it in lucid

sorry: i am not so good at english

---

### Post by dino99 on 2010-06-09
times to times plugins are created and others removed

---

### Post by moseba on 2010-06-09
> **dino99 said:**
> times to times plugins are created and others removed

but these plugins still in the compiz website
[http://wiki.compiz.org/Plugins](http://wiki.compiz.org/Plugins)

---

### Post by cmk24 on 2010-07-17
You can still install the screensaver plugin using git. The first thing to do is install git:

```
sudo apt-get install git
```

Then make a new directory to download the plugin to and install it:

```
mkdir compiz
cd compiz
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
cd screensaver
make
make install
```

NOTE: do not use sudo when you install it, it will install to your home folder so root privileges are not needed.

You can find general instructions for the compiz git repository at [http://wiki.compiz.org/Install/PluginsFromGit](http://wiki.compiz.org/Install/PluginsFromGit) 
You can also find a list of all plugins at [http://gitweb.compiz.org/](http://gitweb.compiz.org/)

Once you turn it on you will have to restart your computer for the changes to take effect. Hope this helps.

---

### Post by AlphaLexman on 2010-07-17
Screensavers are loaded as daemons. The gnome-screensaver is the default for ubuntu. Another good option is 'xscreensaver'. It has many different display modes and imho it is more secure than the gnome version.

---

### Post by joe_newbie on 2010-09-06
This plugin has now been rewritten in C++, the instructions here are not valid anymore. I am looking for a complete howto on the new version of this awesome plugin, and will post them here if I can find some decent instructions.

Joe

---

### Post by dantakeoff on 2011-12-27
[http://www.techdrivein.com/2010/11/script-to-install-incredible-compiz.html](http://www.techdrivein.com/2010/11/script-to-install-incredible-compiz.html)

has the answer...

---

