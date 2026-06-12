---
title: "How to fix CUPS-PDF in Karmic if nothing else worked yet"
date: 2010-04-23
forum: General Help
---

### Post by schongal on 2010-04-23
When I upgraded to Karmic this week (I'm a little slow), of course CUPS-PDF broke, again.  I googled around for fixes.  Most people seemed to be fixing it by running chmod 700 on some cups-pdf files, but that didn't help me at all.  Some people had to uninstall/reinstall cups-pdf, but that didn't help me either.  there was some other hand-waving and magick-making that was also useless.

For me, it turned out to be an apparmor issue.  If you're a noob like me, this may not occur to you immediately.

Here's what I eventually did, and I got it working again.

The quick way: 

```
sudo /etc/init.d/apparmor stop

```
but this turns off apparmor, that's obviously not ideal (but it proved to me that apparmor was the culprit, when cups-PDF suddenly started working)

i went into /etc/apparmor.d and saw the file usr.sbin.cupsd

but there was nothing in the /etc/apparmor.d/disable folder, except a file called usr.bin.firefox-3.5.

so i went into ./disable and executed:

```
sudo ln -s /etc/apparmor.d/usr.sbin.cupsd usr.sbin.cupsd
```

with the intent of making a symbolic link in the /etc/apparmor.d/disable folder, that points to /etc/apparmor.d

then just for good measure I ran

```
sudo /etc/init.d/apparmor restart

```
and now I have full cups-pdf functionality.  Just in time to break it again when i upgrade to Lucid :)

i'm pretty much a linux retard, so i was awfully proud to fix this myself, and i hope it helps anyone else who was frustrated with cups-pdf.  good luck
ms

---

