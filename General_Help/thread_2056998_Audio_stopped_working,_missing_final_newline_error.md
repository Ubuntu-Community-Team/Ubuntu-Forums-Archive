---
title: "Audio stopped working, missing final newline error code (2)"
date: 2012-09-12
forum: General Help
---

### Post by Drew012 on 2012-09-12
Hello, I have been using Ubuntu for about 2 years. I am pretty familiar with a lot of it by now and have basically been solving all of my own problems. However, the other day my audio stopped working after I started using my speakers instead of my headset as my main device. I am guessing I will just have to reinstall the drivers, but that is not the biggest problem. It led me to another problem I get when I try to apt-get something. Whenever I install something I get this at the end:

```

Fetched 1,630 kB in 10s (151 kB/s)                                             
Selecting previously unselected package libglade2-0.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'ttf-droid' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I have used everything in the grub menu and when I test dpkg for errors I get the same error message. I have no idea what 'ttf-droid' is so maybe that is where I should start? Anyways, thank you for your time and I will check back often in case you need more info about my system!

---

### Post by Bashing-om on 2012-09-13
Hi ! drew;

  Take a look in /var/lib/dpkg/status, look for the listing of "ttf-driod" ..
If the status line is other than "install ok installed" ..we can proceed for a fix.

  Chances are dpkg's guiding config file for this file is corrupt.

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Drew012 on 2012-09-13
Hi Bashing-om thanks for the reply,

Here is what I found in the status file:
```

Package: ttf-droid
Status: install ok installed
Priority: optional
Section: oldlibs
Installed-Size: 26
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: fonts-droid
Version: 20101110+git-2
Depends: fonts-droid
Description: transitional dummy package
 This package is a dummy transitional package. It can be safely removed.
Original-Maintainer: Debian Fonts Task Force <pkg-fonts-devel@lists.alioth.debian.org>
Homepage: http://www.ascendercorp.com/pr/2007-11-12/

```
By the looks of it it is all ok

However I found other areas of the status document where 'ttf-droid' was mentioned:
```

Package: fonts-droid
Status: install ok installed
Priority: optional
Section: fonts
Installed-Size: 6066
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 20101110+git-2
Replaces: ttf-droid (<< 20101110+git-2)
Provides: ttf-droid
Conflicts: ttf-droid (<< 20101110+git-2)
Conffiles:
 /etc/fonts/conf.avail/59-droid-serif-fonts.conf bfb17dfd7c9d7cad98dda91347cba203
 /etc/fonts/conf.avail/60-droid-sans-mono-fonts.conf 7d7787d92e7b5089558a6d68c99813e3
 /etc/fonts/conf.avail/65-droid-sans-fonts.conf 7a24b627f856e62dc409e33154487c04
Description: handheld device font with extensive style and language support
 The Droid family of fonts consists of Droid Sans (Regular and Bold),
 Droid Sans Mono (Regular) and Droid Serif (Regular, Bold, Italic and
 BoldItalic).

```
In this second piece of code it appears under 'fonts-droid' and it says something about conflict. Any ideas on what this could be? Hope this helped someone on this as I am pretty lost myself...

---

### Post by Bashing-om on 2012-09-13
Not the result I had expected. However, dpkg (in the original error) advises it is unhappy.

  Let us take dpkg's advise and  fix the offending file. 
```

sudo rm /var/lib/dpkg/info/ttf-droid.list
sudo  apt-get update
sudo apt-get -f install

```As we are advised the package is a "dummy package" and can safely be removed. Let's do so.
the "apt-get update" command also rebuilds dpkg's /info/XXXX  list files.
"apt-get -f install will attempt to fix any broken packages 

Watch for errors..it is probable that other corruption exits; If so, we will do a more thorough house cleaning.

Also, as I am not familiar with fonts, did you install this as a font package, or is ttf-droid a part of the original install ? (as I do not find it on my system, 12.04).[INDENT]tsh <==BDQ

[/INDENT]

---

