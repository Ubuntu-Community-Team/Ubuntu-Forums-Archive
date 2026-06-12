---
title: "Can't unrar split archive."
date: 2010-06-18
forum: General Help
---

### Post by www.com.au on 2010-06-18
I recently downloaded a program to find out it was in pieces. What I originally conceived as being a small problem has turned into a major time wasting dilemma. 

I've tried many different things to get it to properly extract, viewing threads on these forums even, but to no avail.

The files were named:
file.part01.rar
file.part02.rar etc.

I though this was the problem so I renamed all 84 files (except the first one), removing the .rar extension. No cigar.

My final attempt of several was using 7zip:
```
7z x myArchive.rar -o/home/[username]/Desktop
```I was in the correct folder as far as I could tell.

I have included a screenshot of the files in order to stop any confusion about my description. Any help would be highly appreciated as I'm quite anxious to get this working.

---

### Post by Linuxforall on 2010-06-18
Maybe they need to be joined before unrared.

---

### Post by Spr0k3t on 2010-06-18
There's a very good chance a file in the group does not match the MD5 hash check.  If this is the case, you won't be able to open the archive.

Side note: you can download the binary of the installer after logging in to battle.net and skip all of the update patches.

---

### Post by www.com.au on 2010-06-18
Thanks for the help guys, I just might do that (battle.net).

---

