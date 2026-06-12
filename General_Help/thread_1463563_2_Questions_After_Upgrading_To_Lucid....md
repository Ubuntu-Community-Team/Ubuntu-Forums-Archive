---
title: "2 Questions After Upgrading To Lucid..."
date: 2010-04-27
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2010-04-27
I had to reinstall Ubuntu on my desktop PC, so I went and downloaded the 64-bit version of Lucid RC, all seems to be well, except for the fact that my favourite anitvirus, avast! does not seem to be supported on x64 platforms.  Is there a way to force this application to install, as I really like to have it to scan files I send to Windows using friends (and my own Windows install).  I'm using Intel Core 2 Duo E8400

Since I'm using the release candidate of Lucid, as long as I keep up to date, it'll upgrade to the final version on April 29, am I right?  How can I tell whether I'm still using the RC after the 29th?

Thanks in adavnce

---

### Post by rnerwein on 2010-04-27
hi
i have only one question: what the hell you are doing with an antivirus tool on a unix/linux system ???
ciao

---

### Post by clhsharky on 2010-04-27
HI ..::| Dave89 |::..

Enable Medibuntu repos
[http://ubuntuforums.org/forumdisplay.php?f=130](http://ubuntuforums.org/forumdisplay.php?f=130)
refresh repos 
search package manager for " non-free-codecs " install
That gives you the W32 codecs
then try your program again.

Sharky

64bit ubuntu can run 32bit apps, but it needs  w32 codecs to run 32bit apps

---

### Post by ..::| Dave89 |::.. on 2010-04-27
I installed w64 codecs, still says "Error: Wrong architecture 'i386'".

---

### Post by ..::| Dave89 |::.. on 2010-04-27
Answered my own question (again, going to learn to search more thoroughly next time :),  [http://ubuntuforums.org/showthread.php?t=229460](http://ubuntuforums.org/showthread.php?t=229460)

---

### Post by ..::| Dave89 |::.. on 2010-04-27
Sorry, accidentally double posted above message :(

---

### Post by 98cwitr on 2010-04-27
id still love to know what you need AV software for...:confused:

---

### Post by 3rdalbum on 2010-04-27
> **clhsharky said:**
> HI ..::| Dave89 |::..

Enable Medibuntu repos
[http://ubuntuforums.org/forumdisplay.php?f=130](http://ubuntuforums.org/forumdisplay.php?f=130)
refresh repos 
search package manager for " non-free-codecs " install
That gives you the W32 codecs
then try your program again.

Sharky

64bit ubuntu can run 32bit apps, but it needs  w32 codecs to run 32bit apps

Whoa, that's not right. I think you mean "ia32-libs". The w32codecs is for playing certain multimedia files, and they're not available on 64-bit anyway.

You can force the application to install by running:

```
sudo dpkg -i <name of package> --force-architecture
```

(I believe)

Or you can use an archive manager to extract the "data" part of the Debian package, and then manually drag the contents into your filesystem.

---

### Post by 3rdalbum on 2010-04-27
> **98cwitr said:**
> id still love to know what you need AV software for...:confused:

> ...as I really like to have it to scan files I send to Windows using friends (and my own Windows install).

That's what.

---

