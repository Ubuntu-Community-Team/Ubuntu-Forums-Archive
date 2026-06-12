---
title: "install_flash_player_10_linux(2).deb install help"
date: 2009-09-04
forum: General Help
---

### Post by thenoobguru on 2009-09-04
i know theres a ton of these threads about .deb, but i can't make sense of any of them, i keep getting a wrong architecture (i386) error, with all .deb files. is there any fix?

---

### Post by joshuapbell on 2009-09-04
> **thenoobguru said:**
> i know theres a ton of these threads about .deb, but i can't make sense of any of them, i keep getting a wrong architecture (i386) error, with all .deb files. is there any fix?

do you have 64bit or 32bit?

also, it is in the repos, if you go to synaptic and search for flash and select the non-free one it will install flash player version 10

---

### Post by thenoobguru on 2009-09-04
32bit Presario C700

---

### Post by joshuapbell on 2009-09-04
> **thenoobguru said:**
> 32bit Presario C700

what is the exact error?

---

### Post by Vaphell on 2009-09-04
are you sure you have 32bit version of Ubuntu installed?
C700 reportedly has Intel Dual-Core T2390 which is a 64bit architecture.

```
uname -m
``` will answer this question

---

### Post by thenoobguru on 2009-09-04
> **Vaphell said:**
> are you sure you have 32bit version of Ubuntu installed?
C700 reportedly has Intel Dual-Core T2390 which is a 64bit architecture.

```
uname -m
``` will answer this question

frank@ubuntu:~$ uname -m
x86_64
frank@ubuntu:~$ 





when im on vista, it says 32bit thou, does this mean im on a 64bit computer, or 64bit OS,

edit:im postive im not 64bit, i tried to run OSX thou VMWare and had an error saying you need a 64bit computer

---

### Post by gordintoronto on 2009-09-04
> **thenoobguru said:**
> frank@ubuntu:~$ uname -m
x86_64
frank@ubuntu:~$ 


when im on vista, it says 32bit thou, does this mean im on a 64bit computer, or 64bit OS,

Both!

---

### Post by thenoobguru on 2009-09-04
> **gordintoronto said:**
> Both!
ok so now im really confused xD was i running 32bit vista on a 64bit computer?

---

### Post by gordintoronto on 2009-09-04
> **thenoobguru said:**
> i know theres a ton of these threads about .deb, but i can't make sense of any of them, i keep getting a wrong architecture (i386) error, with all .deb files. is there any fix?

What exact version of Firefox are you using?

With 64-bit Ubuntu, I completely failed to get Firefox 3.5 working with Flash, so I reverted to 32-bit Firefox 3.0.13.

---

### Post by Vaphell on 2009-09-04
i don't know about OSX but you have 64bit Ubuntu and firefox -> you need 64bit flash
your computer is 64bit, but it's also backwards compatible with 32bit software, so you can run 32bit version of operating system (as in Vista case)

@gordintoronto
what happened? i had 3.5 working perfectly fine, now 3.6a from mozilla repo
i placed libflashplayer.so manually in proper place and it worked

locate libflashplayer.so => /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by thenoobguru on 2009-09-04
> **Vaphell said:**
> i don't know about OSX but you have 64bit Ubuntu and firefox -> you need 64bit flash
your computer is 64bit, but it's also backwards compatible with 32bit software, so you can run 32bit version of operating system (as in Vista case)

@gordintoronto
what happened? i had 3.5 working perfectly fine, now 3.6a from mozilla repo
i placed libflashplayer.so manually in proper place and it worked

locate libflashplayer.so => /usr/lib/mozilla/plugins/libflashplayer.so

i found a 64bit flash beta, and works tyvm

---

### Post by joshuapbell on 2009-09-05
> **thenoobguru said:**
> ok so now im really confused xD was i running 32bit vista on a 64bit computer?

most modern computers now have 64bit processors, it is mainly a matter of ram more then 3.5 gbs of ram get 64bit os's anything less then that gets 32 bit os's from the manufacturer... although you can install either on it it regardless... I think it is the manufactures way of saving money by choosing the 32 bit os

---

### Post by Liolikas on 2009-09-05
Matter is not only ram. Entire processor "language" is better, updated x86_64 instead of x86. If you use 32bit app on 64bit cpu it mans you can not use entire processor power, beacause program "talks" to it in old Pentium 1 (133Mhz) way.

---

### Post by thenoobguru on 2009-09-06
> **joshuapbell said:**
> most modern computers now have 64bit processors, it is mainly a matter of ram more then 3.5 gbs of ram get 64bit os's anything less then that gets 32 bit os's from the manufacturer... although you can install either on it it regardless... I think it is the manufactures way of saving money by choosing the 32 bit os
so Ubuntu isn't just a better OS, it means i can get more of my computer?

---

### Post by Vaphell on 2009-09-06
there are pros and cons of using 64bit
pros
- boost in speed, especially in math heavy applications
- in theory upper limit of RAM size is almost infinite (2^64), 32-bit = 4GB, no visible gain on machines with less RAM
cons
- programs use more memory (64bit pointers are 2x bigger than 32bit pointers, duh :))
- a lot of programs has no 64bit version (especially in windows land) so there is no advantage in their case

---

### Post by gordintoronto on 2009-09-07
> **Vaphell said:**
> @gordintoronto
what happened? i had 3.5 working perfectly fine, now 3.6a from mozilla repo
i placed libflashplayer.so manually in proper place and it worked

locate libflashplayer.so => /usr/lib/mozilla/plugins/libflashplayer.so

Thanks for your interest.  I forget the details, but it was a shambles.  What I have now works beautifully, so I will stick with it until it's time to go to the next release of Ubuntu.

I'm pretty sure I had a very hard time figuring out where "the right place" was for libflashplayer.so  There doesn't seem to be any consistency from program to program.

---

### Post by Shobuz99 on 2009-09-12
> **Vaphell said:**
> i don't know about OSX but you have 64bit Ubuntu and firefox -> you need 64bit flash
your computer is 64bit, but it's also backwards compatible with 32bit software, so you can run 32bit version of operating system (as in Vista case)

@gordintoronto
what happened? i had 3.5 working perfectly fine, now 3.6a from mozilla repo
i placed libflashplayer.so manually in proper place and it worked

locate libflashplayer.so => /usr/lib/mozilla/plugins/libflashplayer.so

Vaphell,
I tried this manually also, but continued to get "Permission denied" because I am not in root. uh...forgot what to do...complete blank..uh.....then I used 'sudo locate libflashplayer.so => /usr/lib/mozilla/plugins/libflashplayer.so' ... still "Permission denied"... now what?

I'm totally blank.. please slap me, mate! 

Rick (shobuz99)

---

### Post by Shobuz99 on 2009-09-14
Never mind... I got it copied into the /usr/lib/mozilla/plugins folder and then started Firefox and it worked.
Thank you for the information.


Rick (shobuz99)

---

