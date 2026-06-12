---
title: "About compiling Firefox."
date: 2010-09-13
forum: General Help
---

### Post by ron999 on 2010-09-13
Hi
I've recently learned how to compile Firefox from source code.:)
Firefox-4.0b5 'optimized'.

There's information in blogs out on the internet.
But much of this is 'dated'.:icon_frown:

I wonder, do people not bother compiling Firefox these days?
Maybe, now our CPUs are faster and Firefox has improved, it's not worth the hassle.:o

So, do any of you guys compile Firefox yourselves?

---

### Post by s.fox on 2010-09-13
Hello,

I do not, but I did have a look through the source code a couple of months back :)

I think the reason why I do not is that "standard" firefox works perfectly well on my system and I do not have much reason to try and optimize it.  

-Silver Fox

---

### Post by Bobhuber on 2010-09-13
> **ron999 said:**
> Hi
I've recently learned how to compile Firefox from source code.:)
Firefox-4.0b5 'optimized'.

There's information in blogs out on the internet.
But much of this is 'dated'.:icon_frown:

I wonder, do people not bother compiling Firefox these days?
Maybe, now our CPUs are faster and Firefox has improved, it's not worth the hassle.:o

So, do any of you guys compile Firefox yourselves?

Absolutely !!

---

### Post by ibuclaw on 2010-09-13
Compiling from source yourself != optimised. This is a common fallacy.

I have, however, just for fun, once compiled Firefox 3.1 using the Intel C/C++ compiler. ;)

I suppose the next challenge would be using llvm-gcc...

---

### Post by bodhi.zazen on 2010-09-13
I compile icecat for 64 bit arch on a regular basis.

Firefox is a complex application that has many fingers in the OS.

---

### Post by ron999 on 2010-09-13
Thanks for your input folks.

@ bodhi.zazen
Where is the source code for IceCat?

---

### Post by bodhi.zazen on 2010-09-13
> **ron999 said:**
> Thanks for your input folks.

@ bodhi.zazen
Where is the source code for IceCat?

[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

[http://ftp.gnu.org/gnu/gnuzilla/](http://ftp.gnu.org/gnu/gnuzilla/)

This is how I compile it :

[http://blog.bodhizazen.net/linux/icecat-64-bit-how-to-compile/](http://blog.bodhizazen.net/linux/icecat-64-bit-how-to-compile/)

---

### Post by ron999 on 2010-09-14
@ bodhi.zazen
Hi
I followed your directions to compile icecat-3.6.9

```
cd icecat-3.6.9
./configure
make
su -c “make install”

```
It compiles OK, but the command:-
```
su -c “make install”
```
gives me this error:-
> ron@ubuntu:~/icecat-3.6.9$ su -c “make install”
Unknown id: install”

Should I use a different command with Ubuntu?

---

### Post by mc4man on 2010-09-14
> Should I use a different command
just use the typical sudo make install
(it may also work with checkinstall if you wish to try

---

### Post by ron999 on 2010-09-14
Thanks for that mc4man
```
sudo make install
```
did the job. :D
> ron@ubuntu:~$ file /usr/local/lib/icecat-3.6.9/icecat-bin
/usr/local/lib/icecat-3.6.9/icecat-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped


With my clunky Celeron 2.26GHz single core CPU it takes 3 hours to compile. :neutral:
When I compiled Firefox-4.0b5 it took nearly 4 hours. :-k
Looking forward to Icecat-4 ;)

---

