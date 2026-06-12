---
title: "Stupid Question: How to install .bin file?"
date: 2010-06-08
forum: General Help
---

### Post by X-Windows on 2010-06-08
Makes me feel like a tech idiot for not knowing how to do this, but I'll ask anyway. I have had infinite trouble installing .bin files, I have tried everything I could find to no avail. I am currently trying to install Sacred 2, with a 64 bit .bin installer. Here are the steps I tried and their respective errors:

```
cd Downloads
*ls -l  *: Shows file has user as owner and has read/write privileges
sh *filename* - Syntax error: "(" unexpected
./*filename* - Permission denied
sudo ./*filename* - Permission denied

```

Total beginner stuff, but to the best of my knowledge ./ should have run it...

---

### Post by blchinezu on 2010-06-08
```
chmod +x ./filename
```if it's not working use with sudo and then execute.. it doesn't have execute permissions

if we're talking about an installation i suppose you'll have to execute it with sudo

---

### Post by davidmohammed on 2010-06-08
.bin files are usually just executables.  You need to tell it that is an executable though...

in a terminal

chmod +x filename.bin

then

./filename.bin

replace filename with whatever the sacred2 filename is.

---

### Post by X-Windows on 2010-06-08
Thanks, was missing the chmod +x part. Not sure if this related to ubuntu or not, but I get this error when I ./ it - *Initial Lua setup failed. Cannot continue.*

---

