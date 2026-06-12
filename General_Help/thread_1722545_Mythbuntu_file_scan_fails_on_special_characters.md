---
title: "Mythbuntu file scan fails on special characters"
date: 2011-04-05
forum: General Help
---

### Post by rimorob on 2011-04-05
I've got an old linux-based server (a Buffalo Terastation, to be precise) running a non-utf8-capable filesystem (I'm nearly certain).  The main share type is samba.  The server has mangled the foreign characters in all file names, which don't look great when browsing the filesystem.  However, I **can** browse the filesystem from my windows and Mac OS X machines.  

However, when I mount the shared drive from my mythbuntu 10.10 machine (using cifs and, for good measure, iocharset=utf8), I cannot do a successful ls of a directory containing foreign file names.  ls fails after displaying some files, and prints some escape characters on the command line.  Likewise (and this is a mythbuntu specific issue), any attempt to scan the shared folder for files fails after churning for a while (large directory tree).  Undoubtedly, this is the same problem as ls.  

I'm assuming there's a way to mount the shared drive so that ls does no worse than the directory listing in windows or on mac os, just because it's linux, after all, but I can't figure out what to do.  Please help!

P.S. Several posts indicate that using 'iocharset=utf8' will do the trick, but that's only if your server supports utf8.  Mine doesn't - it's a 2004 or 2005 machine - and I don't fancy hacking the ROM.

---

