---
title: "Source packages, mixing releases"
date: 2006-03-15
forum: General Help
---

### Post by gspr on 2006-03-15
Hi.

The one final thing keeping me from switching from Gentoo to Ubuntu, is the ability to pull in bleeding edge packages without doing deep upgrades.
Say, for example, that I am running Breezy and want Firefox 1.5. (I know that this is a bad example, seeing as Dapper is nearly out, but let's say that wasn't the case, for the sake of argument). In Gentoo, I'd emerge firefox, and it would be linked against various GTK and other libraries. No problem. In Ubuntu, I can use pinning to pull Firefox 1.5 from Dapper while keeping an otherwise Breezy system - except for one problem: This firefox is linked against slightly newer GTK and other libraries. Not because Firefox needs these, but because they're shipped with Dapper. Fine enough, but I don't want deep down libraries to be of Dapper versions - that could break my other Breezy packages. So, I start fiddling around with deb-src packages. People keep telling me Debian/Ubuntu does offer all the nicety of Gentoo's source based package system too, and I have no reason to believe otherwise, I just haven't understood it yet.
So anyway, I apt-get source -t dapper firefox. No problem. I enter the source directory, and issue dpkg-buildpackage -rfakeroot -uc -b. OK, it needs a few devel-packages, and some of the ones I have are slightly off-version, some need downgrading - no biggie. At least I don't have to pull in Dapper packages. Then it builds and all is well.
The problem is that when it's done, I don't just get a Firefox deb, I get:
firefox-dev_1.5.dfsg+1.5.0.1-1ubuntu9_i386.deb
firefox-dom-inspector_1.5.dfsg+1.5.0.1-1ubuntu9_i386.deb
firefox-gnome-support_1.5.dfsg+1.5.0.1-1ubuntu9_i386.deb
firefox_1.5.dfsg+1.5.0.1-1ubuntu9_i386.deb
libnspr-dev_1.firefox1.5.dfsg+1.5.0.1-1ubuntu9_i386.deb
libnspr4_1.firefox1.5.dfsg+1.5.0.1-1ubuntu9_i386.deb
libnss-dev_1.firefox1.5.dfsg+1.5.0.1-1ubuntu9_i386.deb
libnss3_1.firefox1.5.dfsg+1.5.0.1-1ubuntu9_i386.deb
mozilla-firefox-dev_1.5.dfsg+1.5.0.1-1ubuntu9_all.deb
mozilla-firefox_1.5.dfsg+1.5.0.1-1ubuntu9_all.deb
, all of which need to be installed in order to install Firefox. Thus, I'm in the same pile of shit I'd be in if I fetched the Dapper Firefox binary - my libraries get non-Breezy-fied. Grr!
What am I missing? I refuse to believe that Debian/Ubuntu isn't able to give me the best of both worlds, I must be missing something.

---

### Post by tioneb on 2006-03-15
Yep you miss something
1- downlaod firefox.tar.gz then

$ cp firefox-1.5.0.1.tar.gz /opt/
$ cd /opt
$ tar xzvf firefox-1.5.0.1.tar.gz
$ rm firefox-1.5.0.1.tar.gz

# to avoid totem plugin trouble
$ cd firefox/plugins/
$ sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
$ sudo rm libtotem_mozilla.*

# to get this version as the default one
$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox
$ sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --\ rename /usr/bin/mozilla-firefox
$ sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

that's done congratulations :)
Besides you still have the old version, not so bad ;)

OUPS I forgot
in the preferred applacations put
firefox %s

---

### Post by gspr on 2006-03-16
Ehm, and where did my debs go in all of this?

---

### Post by tioneb on 2006-03-17
Why do you wanna a deb ? :confused:
sometimes using the tarbal is easier...
you got you new firefox in the folder that YOU specified with the link YOU've done so you can remove everything and you're sure to remove EVERYTHING not like in MS$ \\:D/

---

### Post by gspr on 2006-03-18
Right. You don't have to patronise me. I'm quite well-versed in how to run a GNU/Linux system. I'd just like to learn the Debian/Ubuntu "way of doing things". Thank you for the replies though.

---

### Post by gspr on 2006-03-20
Bumpedibump...

---

