---
title: "Can  I &quot;repair&quot; disk permissions?"
date: 2011-11-03
forum: General Help
---

### Post by asuastrophysics on 2011-11-03
Hey everyone,

I'm getting a weird error in Transmission torrent client that says "unable to save magnet link: permission denied". 

This is a permissions error. On Mac OS X, you can simply repair your disk permissions. Is there any Ubuntu equivalent of this? 

Thanks in advance!! :)

---

### Post by HermanAB on 2011-11-03
Howdy,

Maybe read up on chown and chmod.

---

### Post by asuastrophysics on 2011-11-04
> **HermanAB said:**
> Howdy,

Maybe read up on chown and chmod.

I know a little about those two commands, however they are designed to change folders/files to have the same permissions. On the filesystem, there are many different files with many different sets of permissions. Over time, because EXT3 or EXT4 is like any other unix filesystem, these permissions can be corrupted.

I guess what I'm asking is if there is a program I can install that compares the entire current filesystem's permissions with a list of set default permissions made after a fresh install? Sort of like Mac OS X's Disk Repair Utility?

---

