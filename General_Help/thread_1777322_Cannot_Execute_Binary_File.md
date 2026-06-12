---
title: "Cannot Execute Binary File"
date: 2011-06-07
forum: General Help
---

### Post by wheelern on 2011-06-07
Hey everyone,

I'm trying to install this app called genBlast. It's a bioinformatics tool that does some cool stuff (I guess the actual use doesn't matter that much). Anyway, it comes as a .tar.gz folder with about a dozen executables in it; no compiling necessary. I extracted it to the desktop so I didn't have to worry about permissions, and then just tried to run it from inside the directory (it's a command line app). All of the executables work with a ./ except one, and it's the most important one for that matter. When I go to run it, I get the error message ```
bash: ./genblast: cannot execute binary file

```
I've checked permissions with ls -l, run a chmod 'u+x' just to make sure, and everything else I can think of. But it just won't work.
Also, I just installed it on another computer and it works fine, so I'm pretty sure it's on my end.

Any ideas? The website that hosts the app doesn't have a whole lot of help and support.

---

### Post by linuxinstalledfromhdd on 2011-06-07
Are you trying to use the 32-bit or the 64-bit version of genBlast?

---

### Post by mc4man on 2011-06-07
go - 
 file genblast
And see what it says

Edit: if on a 32 bit install, (likely),  then either move to 64 bit one or use the v136 version instead
(the v138 have a 64 bit  genblast binary in the 32 bit downloads

---

