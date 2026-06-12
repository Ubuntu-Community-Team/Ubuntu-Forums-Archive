---
title: "not able to compile using g++"
date: 2011-08-31
forum: General Help
---

### Post by parth_sharma on 2011-08-31
i am running ubuntu 11.04 natty on AMD athelon 1.68Ghz CPU with with 1gb RAM. i m learning c++ so i am using g++ command to compile, everything was working fine till last 2 days, now i am not able to compile some files, while i can compile other files in the same folder!plz look at the screenshots and help!
[IMG]http://i1085.photobucket.com/albums/j422/parthsharma1996/Screenshot-4-1.png[/IMG]  [IMG]http://i1085.photobucket.com/albums/j422/parthsharma1996/Screenshot-5.png[/IMG]

---

### Post by TeoBigusGeekus on 2011-08-31
Quite strange...
Are you sure the file is there and that you're in the correct folder?

---

### Post by seawolf167 on 2011-08-31
Can you post the output to the following commands please (in the folder where your cpp file is)

```
ls | grep -i phodu
gcc -v -o phodu phodu.cpp
```

---

### Post by parth_sharma on 2011-08-31
@teoBigusGeekus thanks for the help but yeah they are in the same folder,  look at the screenschot carefully!
@seawold166, here is the output:

parth@parth-desktop:~$ ls | grep -i phodu
phodu.cpp 
Phodu.cpp 
parth@parth-desktop:~$ gcc -v -o phodu phodu.cpp
gcc: phodu.cpp: No such file or directory
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
parth@parth-desktop:~$

---

### Post by Slim Odds on 2011-08-31
Try: ```
stat *hodu.*
```

Also, why to you have one with capital P and one without?

---

### Post by seawolf167 on 2011-08-31
> **parth_sharma said:**
> 
@seawold166, here is the output:

parth@parth-desktop:~$ ls | grep -i phodu
**phodu.cpp **
Phodu.cpp 
parth@parth-desktop:~$ gcc -v -o phodu **phodu.cpp**
*gcc:**** phodu.cpp: ****No such file or directory*

Huh... I don't know - the file exists in that directory and is spelled correctly and everything and it sure looks like gcc is working properly.

---

### Post by Cloverfield on 2011-08-31
If it makes you feel any better I have been having the same problem :D

I'll let you know if I figure anything out.

---

### Post by TeoBigusGeekus on 2011-08-31
Could you attach the phodu.cpp somewhere so we could give it a try?

---

### Post by Slim Odds on 2011-08-31
> **TeoBigusGeekus said:**
> Could you attach the phodu.cpp somewhere so we could give it a try?

It's not problem with the files contents. It says that it can't find the file. Most likely an attribute issue. That's why I suggested 'stat'.

---

### Post by parth_sharma on 2011-08-31
@Slim Odds here's the output:

 File: `phodu.cpp '
  Size: 498       	Blocks: 8          IO Block: 4096   regular file
Device: 806h/2054d	Inode: 791022      Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/   parth)   Gid: ( 1000/   parth)
Access: 2011-08-30 21:36:39.653620156 +0530
Modify: 2011-08-29 15:01:17.387876007 +0530
Change: 2011-08-29 15:01:17.387876007 +0530
  File: `Phodu.cpp '
  Size: 498       	Blocks: 8          IO Block: 4096   regular file
Device: 806h/2054d	Inode: 787678      Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/   parth)   Gid: ( 1000/   parth)
Access: 2011-08-31 09:25:47.263751029 +0530
Modify: 2011-08-29 22:45:58.636035499 +0530
Change: 2011-08-29 22:45:58.636035499 +0530
parth@parth-desktop:~$ 
i created two files one with capital letter and other not , bcuz i thought maybe i typed wrong, maybe just an issue of case sensitivity, but that's not the problem!
(by the way i am new to ubuntu forums, hence i do not know BB codes, what is the Bb code for  typying the terminal codE?)

---

### Post by Slim Odds on 2011-08-31
Nothing unusual there...

I'm running out of ideas...

---

### Post by haresear on 2011-08-31
It appears there may be an invisible character in the file names. Are you sure there isn't a blank (space) character in the name following or preceding the visible characters? Does

ls phodu.cpp

show the file exists?

---

### Post by parth_sharma on 2011-09-01
> **haresear said:**
> It appears there may be an invisible character in the file names. Are you sure there isn't a blank (space) character in the name following or preceding the visible characters? Does

ls phodu.cpp

show the file exists?
@haresear
i think you have hit the correct spot!
here's the output:

parth@parth-desktop:~$ ls phodu.cpp
ls: cannot access phodu.cpp: No such file or directory
parth@parth-desktop:~$

---

### Post by haresear on 2011-09-01
Another thing to try is using the tab key to auto-complete the file name, e.g.

ls "phodu.c[tab]"

or

ls "phodu.cpp[tab]"

should auto-complete the file name if it exists. If tab key auto-complete isn't available in the command shell you're using, you can check if the invisible character is a space

ls "phodu.cpp[space]"

or use your file manager to rename the file.

---

### Post by parth_sharma on 2011-09-01
> **haresear said:**
> Another thing to try is using the tab key to auto-complete the file name, e.g.

ls "phodu.c[tab]"

or

ls "phodu.cpp[tab]"

should auto-complete the file name if it exists. If tab key auto-complete isn't available in the command shell you're using, you can check if the invisible character is a space

ls "phodu.cpp[space]"

or use your file manager to rename the file.
hats-off to your reasoning, thanks a lot, problem solved :guitar::P:popcorn::KS

---

