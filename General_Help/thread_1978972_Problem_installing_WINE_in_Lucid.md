---
title: "Problem installing WINE in Lucid"
date: 2012-05-12
forum: General Help
---

### Post by kismul on 2012-05-12
I've recently updated from Karmic to Lucid, with no problems.  I previously had WINE installed, principally to run Spotify.  In Ubuntu Software Centre, I selected WINE Microsoft Windows Compatability Layer and ran INSTALL.  Although it says it's installed, there's no sign of it anywhere on the Applications menu.

Having checked again, I see theat the option I chose is labelled Dummy package.  I've no idea what this does.  There are a number of WINE options available.  Should I have selected something else to actually install WINE?  

Thanks for any advice.

Jim

---

### Post by kismul on 2012-05-13
> **kismul said:**
> I've recently updated from Karmic to Lucid, with no problems.  I previously had WINE installed, principally to run Spotify.  In Ubuntu Software Centre, I selected WINE Microsoft Windows Compatability Layer and ran INSTALL.  Although it says it's installed, there's no sign of it anywhere on the Applications menu.

Having checked again, I see theat the option I chose is labelled Dummy package.  I've no idea what this does.  There are a number of WINE options available.  Should I have selected something else to actually install WINE?  

Thanks for any advice.

Jim

Oops, sorry.  It's the Meta package I have installed, not the dummy package.

---

### Post by JC Cheloven on 2012-05-13
Hi, 

I don't use Spotify myself, but have heard of a native linux version:

[http://www.omgubuntu.co.uk/2011/12/spotify-on-linux-works-for-free-accounts-offers-15-million-tracks/](http://www.omgubuntu.co.uk/2011/12/spotify-on-linux-works-for-free-accounts-offers-15-million-tracks/)

Better than running a win2 version under wine, isn't it?

Hope that helps

---

### Post by flemur13013 on 2012-05-13
Try ```
$ which wine
``` and see what it tells you: it should return something like "/usr/bin/wine".

---

### Post by CatKiller on 2012-05-13
You won't get a menu entry for Wine (what would it do?). You will get menu entries for applications that you install through Wine.

---

