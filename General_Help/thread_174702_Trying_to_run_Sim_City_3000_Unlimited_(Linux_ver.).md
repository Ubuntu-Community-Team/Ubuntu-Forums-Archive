---
title: "Trying to run Sim City 3000 Unlimited (Linux ver.) -&gt; problem!"
date: 2006-05-12
forum: General Help
---

### Post by Norppa on 2006-05-12
I have installed Sim City 3000 Unlimited (for Linux) on Ubuntu, but I cannot get it to start. In the system requirements it says "System: Linux Kernel and glibc 2.1". When I try to start the game in the terminal (I type sc3u to run it) it says: 

"sc3u: relocation error: sc3u: symbol _dl_global_scope, version GLIBC_2.0 not defined in file ld-linux.so.2 with link time reference"

What should I do, anyone please help. This is an older game so is it possible that it does not run on Ubuntu?


*OO-BOON-TOO*

---

### Post by meng on 2006-05-12
Have you tried these instructions?
[http://ubuntuforums.org/showpost.php?p=118657&postcount=16]("http://ubuntuforums.org/showpost.php?p=118657&postcount=16")

---

### Post by Zdravko on 2006-05-12
I didn't know there is a SimCity version for Linux. Where did you get it from? Is it free?

---

### Post by bluenova on 2006-05-16
[QUOTE=Zdravko]I didn't know there is a SimCity version for Linux. Where did you get it from? Is it free?[/QUOTE]
There a quite a few retail games available for Linux. For instance [amazon linux games](http://www.amazon.co.uk/exec/obidos/tg/browse/-/300936/ref=br_bx_1_c_1_0/203-8710532-7350334). No they are not free.

---

### Post by Astinsan on 2007-10-20
Your going to have some problems finding a lot of them. Some were free updates or turned into them. Unreal tournament was a free update. Quake 3 later turned into a free update (although the metal box it comes in was awesome with tux in the corner).

---

### Post by Entity` on 2007-11-12
Ok I did what [this]("http://ubuntuforums.org/showpost.php?p=118657&postcount=16") told me to do and I still got this:

```
user@user-desktop:~/simcity$ sc3u
/usr/local/games/SC3U/sc3u: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
/usr/local/bin/sc3u: line 2: EOF: command not found
```

except I left this out in the step 10:

```
#!/bin/bash
```

did I screw myself?  is it fixable?

Edit:
I even redid steps 10 and 11 leaving nothing out.
still got the same thing

<snip>

---

### Post by Entity` on 2007-11-13
Anyone have an answer?

---

