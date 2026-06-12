---
title: "screen saver /slide show  12.04"
date: 2012-04-28
forum: General Help
---

### Post by harvledger on 2012-04-28
I can't find screen saver in 12.04.  :>(

---

### Post by GameX2 on 2012-04-28
Hi,


First, remove Gnome-Screensaver, which is obsolete, well, not going to be useful in this case:

```
sudo apt-get remove gnome-screensaver
```

Then install XScreenSaver:

```
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
```

Start Xscreensaver like any other program, from Unity dash.  Enjoy. ;)

Dont forget to add the command ```
xscreensaver -nosplash
``` in your startup applications, otherwise it won't work proprely!

---

### Post by kawabago on 2012-04-29
I would add "Type 'startup app' in Dash Home (top of Dashboard on left)".

---

### Post by balbecdaze on 2012-04-30
I got this:

Package xscreensaver is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xscreensaver-data

Package xscreensaver-data-extra is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xscreensaver-data

Package xscreensaver-gl-extra is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xscreensaver-gl

E: Package 'xscreensaver' has no installation candidate
E: Package 'xscreensaver-gl-extra' has no installation candidate
E: Package 'xscreensaver-data-extra' has no installation candidate

So, replace terminal code with

```
 sudo apt-get install xscreensaver-data xscreensaver-gl
```

---

### Post by balbecdaze on 2012-04-30
Aah a quick

```
sudo apt-get update
```

and problem solved!

---

### Post by sharinoumi on 2012-05-14
I have installed xscreensaver and all others, removed gnome screensaver.
xscreensaver is already the newest version.
xscreensaver-data-extra is already the newest version.
xscreensaver-gl-extra is already the newest version.
However, I cant get the slideshow, xscreensaver-demo gives the following error messages:

(xscreensaver-demo:3095): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory
glslideshow: unable to load font "-*-helvetica-medium-r-normal-*-180-*", using "fixed"
Can't locate LWP/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/bin/xscreensaver-getimage-file line 53.
BEGIN failed--compilation aborted at /usr/bin/xscreensaver-getimage-file line 53.

Can one help me?

---

### Post by sharinoumi on 2012-05-14
> **sharinoumi said:**
> I have installed xscreensaver and all others, removed gnome screensaver.
xscreensaver is already the newest version.
xscreensaver-data-extra is already the newest version.
xscreensaver-gl-extra is already the newest version.
However, I cant get the slideshow, xscreensaver-demo gives the following error messages:

(xscreensaver-demo:3095): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory
glslideshow: unable to load font "-*-helvetica-medium-r-normal-*-180-*", using "fixed"
Can't locate LWP/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/bin/xscreensaver-getimage-file line 53.
BEGIN failed--compilation aborted at /usr/bin/xscreensaver-getimage-file line 53.

Can one help me?

So I found that 
sudo apt-get install libxml-simple-perl

solves the problem.

---

