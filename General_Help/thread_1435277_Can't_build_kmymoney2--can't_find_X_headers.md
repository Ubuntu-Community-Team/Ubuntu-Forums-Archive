---
title: "Can't build kmymoney2--can't find X headers"
date: 2010-03-21
forum: General Help
---

### Post by thorpflyer on 2010-03-21
Hi all,

Apologies if this is the wrong list, I'm new here.

I'm trying to build KMyMoney2 on Ubuntu 9.04, and I've gotten past a bunch of minor issues (installed the KDE stuff, installed GCC, and something else that I now forget). However, I now have an issue that's got me stuck; it claims it can't find the X headers. (I realize this is an Ubuntu forum, but this is a "standard" gnu type build, and it's the ./configure that's doing the complaining, so I figure this might not be inappropriate.)

The headers I think it's looking for are present in the usual place /usr/include/X11/. Of course, I don't know if it's actually looking for something different or a particular header that's missing. I can't see any X headers or development stuff that's not installed on this system, and I've tried adding the flag --includedir=/usr/include/X11 but that didn't change anything.

Any thoughts anyone? Or any better forum to ask the question in? (I have asked on the KMyMoney list but I don't know which end of the pairing is more relevant :)

Oh, btw, I know that Ubuntu has KMyMoney2 version 9.something, but I really want to build the latest (1.0.3) for some features it has, and I can't find a pre-build binary either.

TIA,
Simon

---

### Post by ellgor on 2010-03-21
Hi,

It could be Libx11-dev, that contains header files.

Regards, Ellgor.

---

### Post by thorpflyer on 2010-03-21
Hi, Thanks for the suggestion. That package is already installed. As I said, I'm pretty sure the headers are there (I've a bunch of vaguely familiar looking stuff in /usr/include/X11) but the configure system doesn't seem to find them. (Or maybe it's generating the wrong error message!)
Cheers,
Simon
\

---

### Post by thorpflyer on 2010-03-21
OK, turns out that I can get the necessary packages using:

apt-get build-dep kmymoney2

After that I have to ./configure --without-arts so that it doesn't blow up on some old something I don't understand.

But it's building now, so hopefully this is solved. Thanks all for your help.

Cheers,
Simon

---

