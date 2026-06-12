---
title: "Is it a good idea to install gcc-4.5?"
date: 2010-12-27
forum: General Help
---

### Post by outofsync on 2010-12-27
Is it a good idea to install gcc-4.5 in Maverick, or can I break something by installing it? I checked that I've gcc-4.4.4, which seems to be the default version installed in Maverick.

Honestly, I don't need to be on the latest gcc version, but I've read here about a bug in gcc-4.4 which affects Wine, and I'm going to cross-compile win32 apps from ubuntu, so I wish to get rid of that bug. Look about the bug here (read the section "using an up-to-date gcc"):
[http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64)

If it's safe to install 4.5 on Maverick, what packages should I install? Should I take care of anything while upgrading? What must I do? Note that I installed support for compiling 32 bit executables from x64 (I'm on x64 ubuntu).

Thanks a lot in advance,

outofsync

---

### Post by tredegar on 2010-12-27
I don't think you can run stuff that has been compiled by a version of gcc that is newer than the version your kernel was compiled by. 

The verson of gcc you have installed will be the version your current kernel was compiled by.

I tried this once, waaaay back, and ended up having to restore my "workhorse" computer from a full backup I sensibly took before I started.

"Never again" :(

If you are determined to give it a try:
- Take a full backup before you start. Make sure you know how to restore it.
- Test **gcc-4.5** on a virtual or spare machine.
- Do both!

Have fun.

---

### Post by outofsync on 2010-12-27
Thanks a lot for your comment, tredegar. I believe you saved me from quite a few nightmares ;)

Btw, is there some way of checking if this bug is already fixed on gcc-4.4.4, or if there's some way of fixing it? :
[http://gcc.gnu.org/bugzilla/show_bug.cgi?id=43869](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=43869)

Thanks!!

---

### Post by mc4man on 2010-12-27
In maverick gcc-4.5 is available and will cause no issues if installed, your default gcc will remain gcc-4.4.
To use will depend on the source as to the method for specifying a gcc other than the default.
It may be as simple as CC=gcc-4.5 ./configure ect. or you may need other means
Ex. for ffmpeg, it uses a configure option, so adding --cc=gcc-4.5 produces 
> CC_IDENT=gcc 4.5.1 (Ubuntu/Linaro 4.5.1-7ubuntu2)
ARCH=x86
CC=gcc-4.5
AS=gcc-4.5
LD=gcc-4.5
DEPCC=gcc-4.5


For your wine I'd first try adding like this and see what the configure produces
./configure --enable-win64 CC=gcc-4.5 .ect

---

