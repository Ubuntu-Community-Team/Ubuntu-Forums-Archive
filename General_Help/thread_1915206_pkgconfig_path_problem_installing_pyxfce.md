---
title: "pkgconfig path problem installing pyxfce"
date: 2012-01-25
forum: General Help
---

### Post by jesuisbenjamin on 2012-01-25
Hello,

I am trying to install [pyxfce]("http://pyxfce.xfce.org/") on Xubuntu 11.10.

While running [FONT="Courier New"]./configure[/FONT] the error returns:

```
checking for libxfcegui4-1.0 >= 4.3.90... not found
*** The required package libxfcegui4-1.0 was not found on your system.
*** Please install libxfcegui4-1.0 (atleast version 4.3.90) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.
```

I first made sure the package was installed with:
```
sudo apt-get install libxfcegui*
```

Then I found out where all the pkgconfig paths are:
```
find /usr -name "pkgconfig"
```
Then I passed the output to the path variable and exported it:
```
PKG_CONFIG_PATH=/usr/share/pkgconfig/:/usr/lib/i386-linux-gnu/pkgconfig/:/usr/lib/pkgconfig/
export PKG_CONFIG_PATH
```

Running [FONT="Courier New"]./configure[/FONT] again however, didn't go any better.

What am I missing here?

---

