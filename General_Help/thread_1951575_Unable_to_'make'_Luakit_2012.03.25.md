---
title: "Unable to 'make' Luakit 2012.03.25"
date: 2012-04-02
forum: General Help
---

### Post by Earsplit on 2012-04-02
I love luakit.  It is the perfect browser to me.  However the one in the ubuntu repositories is kind of outdated (august 2011), and I'd like to update.  It seems to be spiking my CPU up to 100% on some flash websites.

When I try to 'make' inside the folder, i get the following output:
```

config.mk:42: *** Unable to determine lua pkg-config name, specify manually with `LUA_PKG_NAME=<name> make`, 
  use `pkg-config --list-all | grep lua` to find the correct package name for your system.
  Please also check that you have lua >= 5.1 installed.  Stop.

```

Yet, I have both the packages lua and lua5.1 installed.  pkg-config does not seem to list them.

Any ideas?

---

### Post by Toz on 2012-04-02
I tried this a while back and was only being able to get so far. 

You're going to need:
- **liblua5.1-0-dev**
- **libsqlite3-dev**
- **libwebkitgtk-3.0-dev**
- **libwebkitgtk-dev**
...and
- **libjavascriptcoregtk-1.0-dev**. However, this package is not available in natty (11.04) or oneiric (11.10), but it does look like its available in precise (12.04).

There is also a webkit PPA ([https://launchpad.net/~webkit-team/+archive/ppa]("https://launchpad.net/~webkit-team/+archive/ppa")) that apparently has the file available, but I stopped short of installing that PPA.

---

### Post by Earsplit on 2012-04-03
Thanks for you help.  I'll stick with the outdated version for now, using chromium + vim extensions for heavy javascript.

To all developers: please add an updated luakit to the 12.04 repos.  Try it out and you'll know why :p

---

### Post by oldos2er on 2012-04-03
> **Earsplit said:**
> To all developers: please add an updated luakit to the 12.04 repos. 

You should post this at brainstorm.ubuntu.com. It's highly unlikely any developers will see it here.

---

