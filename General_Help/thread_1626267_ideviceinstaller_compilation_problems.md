---
title: "ideviceinstaller compilation problems"
date: 2010-11-20
forum: General Help
---

### Post by Bear-Lt on 2010-11-20
Hello!
Since yesterday I've been trying to get *ideviceinstaller* compiled and I still can't do it. I was following this guide:
[http://ubuntuforums.org/showthread.php?t=1471018](http://ubuntuforums.org/showthread.php?t=1471018)
When compiling (*make*) *ideviceinstaller* I get version missmatch error:
> libtool: Version mismatch error. This is libtool 2.2.6, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6b.
libtool: You should recreate aclocal.m4 with macros from libtool
libtool: and run autoconf again.
What should I do? I've already tried autoreconf, aclocal, download various package versions via git, download tarball. Nothing helped. My libtool version is 2.2.6b. Ubuntu 10.10.

---

### Post by Bear-Lt on 2010-11-20
News: problem fixed! The solution was found by Nikias @ IRC FREENODE #libimobiledevice
The solution is:

> 
git clone [http://git.sukimashita.com/ideviceinstaller.git](http://git.sukimashita.com/ideviceinstaller.git)
cd ideviceinstaller
./autogen.sh --prefix=/usr
make && sudo make install

"--prefix=/usr is Ubuntu/Debian specific. You could omit that."


Problem solved!

---

