---
title: "xclip install problems"
date: 2006-05-07
forum: General Help
---

### Post by Seth Williamson on 2006-05-07
Because I'm on a prehistoric dial-up connection at home, I frequently use the fine text-based browser elinks.  On this page

[http://edulinux.homeunix.org/elinks/](http://edulinux.homeunix.org/elinks/)

I found some tips about configuring elinks to pass urls (see the section called URI-passing).

When I set it up as described, I got an error message:

sh: xclip: command not found

I figured that meant I didn't have it installed.  So I did apt-get install xclip and watched it download and install.

However, I'm STILL getting the same error message.  When I do

which xclip

I get nothing--it just goes back to the prompt.

When, just for the heck of it, I try to reinstall it, I get

root@orthobox:/home/seth# apt-get install xclip
Reading package lists... Done
Building dependency tree... Done
xclip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

which would seem to suggest that it's already installed.

But why am I getting the error message as if it's not there?

Could it not be in my path?  I don't understand why not, since every program I've ever installed is in the path and runs properly.

Just FYI, I'm running Kubuntu.  I have klipper running, though I don't see what difference that would make.

Anybody have any ideas how to make this work?


Seth Williamson
Slings Gap
Franklin County, VA
USA

---

