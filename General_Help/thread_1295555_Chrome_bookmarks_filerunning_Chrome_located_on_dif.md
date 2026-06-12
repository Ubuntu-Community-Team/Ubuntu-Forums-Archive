---
title: "Chrome bookmarks file/running Chrome located on different partition from a live boot"
date: 2009-10-19
forum: General Help
---

### Post by Donhcd on 2009-10-19
Hello all,

I had been using 9.10 alpha5, but after an update, the OS stopped responding to my keyboard and mouse. I once got access to a terminal, but I'm kind of new to Linux, so I figured I would try one of the "recover" options from the boot menu. I'm not sure if I did something wrong, but the recover option seems to have gotten rid of some fundamental parts of the OS and I've pretty much given up on it.

Anyways, I am now trying to salvage the things I had on there before so that I fill up that partition with a new version of Linux, and one of the most significant things I want are my Chrome bookmarks. I can still access the files I had on there, so I got the files in the Home folder that seemed important backed up. However, I can't find the Chrome bookmarks file that I think should be somewhere. Does anybody know if the mythical bookmarks file exists and where it is?

Also, I was thinking that it might be possible to try to run the Chrome on my old dead Ubuntu from a Knoppix or Ubuntu live boot CD and just create a bookmarks file on there the normal way. The main problem is I'm not sure where exactly where the chrome executable is located. Right now, I'm just file-searching on Nautilus for "Chrome" in that drive, but I'm not getting the correct executables.

If anybody can help me with any of this, I would greatly appreciate it. Thanks a lot!

Regards,
Don

---

### Post by Vostrocity on 2009-11-09
Not to revive an old thread, but I feel this is very important. I also had trouble finding this file and surprisingly there was absolutely no information about this for Chrome on Linux. After scourging around a bit I have found it in "/home/{username}/.config/google-chrome/Default". So here it is for anyone else stumbling upon this thread in the future.
:D

---

