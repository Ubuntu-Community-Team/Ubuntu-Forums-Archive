---
title: "Best way to install"
date: 2010-07-03
forum: General Help
---

### Post by jesuisbenjamin on 2010-07-03
Hell there,

i'd like to install this python graphic library (cgkit) [http://sourceforge.net/projects/cgkit/files/cgkit/](http://sourceforge.net/projects/cgkit/files/cgkit/)

I'd like to know what is the best way to install this. Can i add this to my repositories although it is not a .deb file? Should i un-tar and move the files manually? If so where?

Thanks.
B.

---

### Post by Joe of loath on 2010-07-03
You'll have to compile it, as it's distributed as source code. Instructions should be in the archive.

---

### Post by drpjkurian on 2010-07-03
> **jesuisbenjamin said:**
> Hell there,

i'd like to install this python graphic library (cgkit) [http://sourceforge.net/projects/cgkit/files/cgkit/](http://sourceforge.net/projects/cgkit/files/cgkit/)

I'd like to know what is the best way to install this. Can i add this to my repositories although it is not a .deb file? Should i un-tar and move the files manually? If so where?

Thanks.
B.
Hi
I suggest you to install by installing it with checkintall
By this procedure you can create .deb file tooo. So that anyone else can install it easily by sharing your .deb

---

### Post by jesuisbenjamin on 2010-07-03
thanks i'll try that last one.

---

### Post by jesuisbenjamin on 2010-07-03
According to the instructions i need a package called Boost to make the file. But apt-get can't find any Boost package.

Also, a .deb file should be available according to [http://cgkit.sourceforge.net/download.html](http://cgkit.sourceforge.net/download.html) (cf. bottom of page)

But even after adding the repository (which looks odd to me), apt-get can't find the libcgkit deb file.

Any advice?

---

### Post by jesuisbenjamin on 2010-07-05
Anyone with tips? Thanks :)

---

### Post by mprice on 2010-07-05
Thats because that repository listed is for Debian not Ubuntu. I found a ppa repository that has cgkit here: [https://launchpad.net/~astraw/+archive/ppa]("https://launchpad.net/%7Eastraw/+archive/ppa")

---

