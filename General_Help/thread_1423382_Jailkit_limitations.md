---
title: "Jailkit limitations"
date: 2010-03-06
forum: General Help
---

### Post by noone123 on 2010-03-06
Hi!
I have Ubuntu server x64 and I set up a chroot jail with an easy application called Jailkit, the version isn't the newest one, but the one which was used in a tutorial that is also in this forum.
So the thing is that I have a jailed user and I want him to run a server from there (a .bin file) but when I do that I get "No such file or directory", of course there is this file, but using ./file.bin doesn't work, but ./file.sh works fine!
So I'm missing something or there is a limitation that doesn't allow me to run .bin files.
Can this limitation be removed or missing file be added?

---

### Post by rnerwein on 2010-03-06
hi
what does the command: file ./file.bin tells you ?
i guess it's an intermidiate code.
ciao
oh i just see you run a x64 system - i guess ubuntu is 64bit too. 
ldd will show you if some 32bit libs are missing.
 i had a similar problem with gcc and have to install
apt-get install ia32-libs
apt-get install gcc-4.4.multilib
in order to create 32bit executables.

---

### Post by noone123 on 2010-03-06
Outside the jail:
```
file.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
```

---

### Post by rnerwein on 2010-03-07
hi
try: ldd file.bin - and have a look if all the libraries the process needs are present.
( on the other side i don't understand why it is running with file.sh ?? - another environment ?
ciao
oh i just see you run a x64 system - i guess ubuntu is 64bit too. 
ldd will show you if some 32bit libs are missing.
 i had a similar problem with gcc and have to install
apt-get install ia32-libs
apt-get install gcc-4.4.multilib
in order to create 32bit executables.

---

### Post by noone123 on 2010-03-07
Outside the jail everything is fine.
But inside the jail I can't run this .bin file (forgot to tell that I haven't tried other files), so I guess the problem is that jail is in 64-bit but the .bin file is in 32-bit.
Then I need to copy libraries that are needed to run 32-bit files in the jail.
Also this in jail:
```
ldd file.bin
        not a dynamic executable
```
and outside the jail:
```
file file.bin
dynamically linked (uses shared libs)
```
How can I know what are the libraries that I need to copy?

You were right, I needed 32-bit libraries in order to run 32-bit apps in jail.
So I copied /usr/lib32 (not a good idea?) to jail and I was able to run.
It is dumb that I forgot that I'm trying to run 32-bit app not a 64-bit one, but why not simply give an error about it?
Anyway thanks!

---

### Post by rnerwein on 2010-03-07
hi
if it's running now - be happy.
but by the side - you are not a dump the dump is jailkit because they don't thought about the situation
of a mixture 32 / 64 bit. normaly there should be no problem from 32 to 64 bit.
on the other side: ldd must miss something else because it gives you the output: 
 not a dynamic executable
hope there don't come more problems.
to copy the 32 bit libs was ok.
ciao

---

