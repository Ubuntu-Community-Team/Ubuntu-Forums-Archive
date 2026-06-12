---
title: "after today's updates, firefox won't run anymore  -- seeking guidance"
date: 2009-11-13
forum: General Help
---

### Post by networkspeedy on 2009-11-13
After the auto-updates ran today I could no longer run firefox unless I ran it with gksu (root).  That's not acceptable of course, so I was wondering what tips I might get in this situation.  Does anyone know what could be causing this failure?  Details follow below.

Things I've already done:
Attempt #1:
[LIST=1]
[*]backed up my ~/.mozilla folder
[*]dpkg --purge'd all packages matching `dpkg -l|grep -i firefox`
[*]dpkg --purge --ignore-depends=... all packages matching `dpkg -l| grep i xulrunner`
[*]rm -rf'd any directories left over, like /usr/lib/firefox*
[*]apt-get clean'd
[*]reinstalled all packages fresh from the repo via apt-get
[/LIST]
FAIL: the above didn't work

Attempt #2:
[LIST=1]
[*]run `strace firefox` and look for errors; compare output with the output of...
[*]...`sudo strace firefox`
[*]I observed that firefox blocked when run without sudo, right around a failure to find libxpcom.so under /usr/lib/firefox/xulrunner
[*]When firefox runs as root, it doesn't find it there either, but falls back to the library directory for xulrunner itself and marches on.
[*]I looked on my system for libxpcom.so and found it under the lib directory the xulrunner package
[*]I made a symlink to the xulrunner directory under /usr/lib/firefox...
[*]re-ran `strace firefox`
[*]I saw that xulrunner libxpcom.so was found, however the process still blocked before the firefox window ever opened.
[/LIST]
FAIL: the second attempt didn't work either.

I removed the xulrunner symlink after this second failure, not wanting to leave something in place that wasn't part of a default clean install.

For what it's worth, the strace for running firefox as my regular user, without the xulrunner symlink is attached.  It does not complete, because at the last instruction shown in the strace, it just hangs.

Ideas?

TIA,
-tommy

---

