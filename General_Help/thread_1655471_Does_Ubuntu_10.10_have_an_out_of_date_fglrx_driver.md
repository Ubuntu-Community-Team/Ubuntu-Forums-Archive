---
title: "Does Ubuntu 10.10 have an out of date fglrx driver?"
date: 2010-12-29
forum: General Help
---

### Post by s3a on 2010-12-29
The terminal tells me that the version in 10.10 is:
2:_8.780_-0ubuntu2 but isn't the latest version: _10.12_?

To keep up to date do I need to install the driver from AMD's website or has Ubuntu changed the numbering around or something?

Any input would be appreciated!
Thanks!

---

### Post by s3a on 2010-12-29
I just realized that 8.801 means 10-12. Why are there different numbers and what do the differences mean?

---

### Post by hawthornso23 on 2010-12-29
Unless you have a problem with the way your video is working, I wouldn't advise you to install fglrx from the ATI website for the following reasons


[LIST=1]
[*]In my experience the latest fglrx driver often has bugs. It isn't officially called beta software, but probably should be treated that way. Updating fglrx can cause bizarre problems. See for example [ http://ubuntuforums.org/showthread.php?t=1647385]("http://ubuntuforums.org/showthread.php?t=1647385") . The version installed by the repositaries is more certain to be stable.
[*]Installing the ATI drivers manually is a tricky process with considerable scope for things to go wrong. The instructions on the ATI website are confusing and at times out of date. At the moment there is a decent set of instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide) but there is no guarantee that these will stay up to date.
[*]Uninstalling is also tricky.
[*]If you install yourself, then whenever you get a kernel update it is probably going to break your fglrx driver and you'll have to reinstall. Using the repositaries it SHOULD update automatically (although I have seen this fail as well).
[*]A lot of what updates are doing is accommodating new hardware. If your hardware is working OK then you probably don't need it.
[/LIST]
Unless you have a real reason for doing it, it probably isn't worth the hassle.

---

### Post by s3a on 2011-01-01
Actually the upstream installer now compiles deb files for you! The reason was because my graphics don't perform as well as they do in Windows although they're still good enough. If someone knows why there are different numbering schemes and what the differences mean, I'm still interested.

---

