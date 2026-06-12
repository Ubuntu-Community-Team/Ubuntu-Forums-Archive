---
title: "segfaults in some applications, leaving a libc error in dmesg"
date: 2012-06-25
forum: General Help
---

### Post by hkzlab on 2012-06-25
Hello everyone,
I'm a bit lost on this one, never got something like this in my years of linux experience.
Yesterday evening I updated all the packages on my desktop pc (Ubuntu 12.04, amd64, core 2 duo processor) as it was behind a few weeks. Apparently everything went well, the PC powered down fine after I finished. But when I turned it on today I got a nasty surprise: a lot of applications die with a segfault, leaving an error like this in dmesg:
```
[  185.594356] gimp[3167]: segfault at 7f7c6bc59bf0 ip 00007f7b98eb8fd8 sp 00007fff43d601e8 error 4 in libc-2.15.so[7f7b98d7d000+1b3000]
```That one is gimp, but I get similar errors with compiz and evolution (the common thing is error 4, libc-2.15.so and the memory offset of 7f7b98d7d000+1b3000).

Here is what i tried:

[LIST=1]
[*]Thinking that libc-2.15.so might have gotten corrupt, I reinstalled the libc6 and libc-bin packages directly from the deb files, that didn't help
[*]suspecting a filesystem corruption, I forced a fsck on boot (/forcefsck). That didn't find anything.
[*]suspecting a RAM problem, I ran memtest86 for a few hours. No memory problems at all
[*]To check that my processor was still working fine, I tried compiling a relatively heavy project (scummvm) with a -j4 option to use both cores. It compiled fine and the resulting code was working.
[/LIST]
I'm left with absolutely no ideas... Anyone has one?

---

### Post by dino99 on 2012-06-25
if you have some alpha/beta package(s) from ppa, then purge these ppa first (ppa-purge .....), then logout/in

and 

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by hkzlab on 2012-06-25
Thanks for the idea.
It's finding some broken packages which I'm fixing one by one (either reinstalling them or removing them when not needed). 
I'll let you know if it fixes the main problem once i finished.

---

### Post by hkzlab on 2012-06-25
Sadly it didn't work: the problem shows up exactly as before.
Also, I tried running ubuntu 12.04 using the livecd, and gimp starts fine there.

Any more ideas?

---

### Post by hkzlab on 2012-06-25
Well, believe it or not, it was an icon problem.
The icon-theme.cache file in /usr/share/icons/gnome got corrupted in some way... I found out after looking at the output of strace and valgrind while running gimp (the code was dying on a strcmp while reading the index file).
I removed that file and regenerated it by reinstalling the gnome icon packages: everything is fine now.

---

