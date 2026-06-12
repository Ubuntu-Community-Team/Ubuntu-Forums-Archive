---
title: "newer version of adobe installed"
date: 2010-02-03
forum: General Help
---

### Post by childofGod on 2010-02-03
I'm trying to install adobe flash player so that I can stream hulu on my desktop which is running hardy heron.  Adobe's download center wants to download Adobe Flash Player version 10.0.42.34 for Linux and install it with the GDebi installer.  When I go through this process it gives an error message saying a newer version than this is already installed.  I don't know how this happened but whatever the newer version is doesn't work.  Can someone explain to me how to troubleshoot this issue?

---

### Post by Leppie on 2010-02-04
i believe hulu doesn't like the flash for linux (i cannot confirm this personally as i've never used hulu).
however, are other flash sites working properly? try sites like youtube, facebook, etc. if those work, your flash plugin is working properly.

---

### Post by slakkie on 2010-02-04
Flash on Hardy is up2date:

```

     10.0.42.34-2 0
        990 http://archive.canonical.com hardy/partner Packages

```

You can view this by running apt-cache policy adobe-flashplugin in a terminal.

---

