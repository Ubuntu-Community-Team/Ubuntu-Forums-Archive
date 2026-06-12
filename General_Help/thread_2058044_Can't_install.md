---
title: "Can't install"
date: 2012-09-14
forum: General Help
---

### Post by Darkish Dave on 2012-09-14
Hello,

I can't install and distro using the Wubi method.

I get a error message after the distro downloads to check the log.

I unable to see what's wrong and need some help resolving the issue. 


Anyway here is the log: [http://pastebin.com/2rUQg3He](http://pastebin.com/2rUQg3He)

Also, I tried running Wubi and the downloaded distro in the same folder with no luck. Wubi just downloads a new iso.

---

### Post by bcbc on 2012-09-15
> 09-15 00:31 DEBUG  Distro: wrong version: 12.04 != 12.04.1

What this means is that Wubi.exe has been bumped to 12.04.1 and it requires a 12.04.1 version of the ISO, but lubuntu didn't release a 12.04.1 ISO, so... Wubi downloads the 12.04 lubuntu ISO and then thinks it's invalid.

You'll need the 12.04 version of wubi.exe which is no longer available except from within the ISO or from here: [http://people.canonical.com/~evand/wubi/precise/wubi-r266-signed.exe](http://people.canonical.com/~evand/wubi/precise/wubi-r266-signed.exe)

Here's a bug report: [https://bugs.launchpad.net/wubi/+bug/1043607](https://bugs.launchpad.net/wubi/+bug/1043607)

---

