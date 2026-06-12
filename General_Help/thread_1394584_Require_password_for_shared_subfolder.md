---
title: "Require password for shared subfolder?"
date: 2010-01-30
forum: General Help
---

### Post by BrutalSpoon on 2010-01-30
Hi guys,

The server which I'm building is very nearly complete. There's a couple of things left to do, most of which I've found help for already.

One thing I would like to do, though, is password protect a subfolder of a shared volume.

E.g. I have a documents partition, and inside the partition I have a subfolder with some private documents. I could set up a brand new partition, but the problem with that is that chances are the partition will either be too large or too small, wasting disk space or causing hassle when I need to resize it and make it larger. So, I want to just be able to lock this subfolder. Is there a way to do this?

I tried EncFS, but although it works perfectly on the server itself, when I connect to the volume from my other PC running Windows 7 over samba it simply doesn't see the folder at all (which kinda defeats the purpose).

Admittedly, I COULD access the files directly on the server using VNC, but that's a lot of extra hassle, and I'd really prefer to be able to access the files from other computers. I just want to be able to secure them with a password so that only I can access them.

Any ideas?

Thanks in advance (as always),

BrutalSpoon

---

