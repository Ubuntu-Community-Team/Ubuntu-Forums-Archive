---
title: "how to add custom .7z settings as default"
date: 2011-02-17
forum: General Help
---

### Post by debd on 2011-02-17
the archive manager in ubuntu uses default settings for archiving files into .7zip 

s. but much more compression can be achieved setting the cmpression level 

higher from command line. Is there a way I can set that settings as default in 

Archive manager?

---

### Post by debd on 2011-02-17
well, for everyone here is a great site that helps genarate your custom command for creating 7zip archieves.

[http://www.howtoadvice.com/7zipHelper](http://www.howtoadvice.com/7zipHelper)

check out!

---

### Post by seawolf167 on 2011-02-17
If you are familiar with the command line, the easiest thing may be to simply make an alias:

```
vi ~.bashrc
```

Then scroll down to the alias section and add your custom command line alias like:

```
alias zz="some 7z command parameters"
```

---

### Post by debd on 2011-02-18
well, the idea is good. but I'm not sure enough how to form the alias. bcoz the compression level argument is to be appended at the last i.e. after the output and input path.

can you help?

here is a e.g. of the command

```
7z a -t7z /home/user/Desktop/uu.7z /home/user/pi.txt -mx9
```

/home/user/Desktop/uu.7z iis the output file
/home/user/py.txt is the input file
-mx9 is the compression level

---

### Post by seawolf167 on 2011-02-18
From the 7z man page, the compression level switch can come before your location arguments:

```
man 7z

Example 1:
7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on archive.7z dir1
*adds all files from directory "dir1" to archive archive.7z using "ultra settings"*
```So an alias for that command could be similar to:

```
gedit ~.bashrc
```Scroll down to the alias section, add the line

```
alias vv="7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on"
```Then save, exit your terminals and reopen them. Now, in a terminal you can type 

```
vv archive.7z dir1
```

for the exact same effect as

```
7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on archive.7z dir1
```

---

### Post by debd on 2011-02-18
thank you buddy. I didn't know it.

---

