---
title: "Wich kernel to use for a P4 with hyper threading?"
date: 2010-05-26
forum: General Help
---

### Post by cain071546 on 2010-05-26
p4 2.6HT after removing XP media center i installed lucid from live cd. It shows 2 processors at 2.6 each usinng kernel 2.6.32-22 generic pae. but feels a bit sluggish my other p4 2.0ghz with no HT seems to run better with less ram as well . After searching Google i found out about the smp kernel. Should i use it?     
after checking installed kernels this is the output

  ian@ian-desktop:~$ dpkg --list | grep linux-image
ii  linux-image-2.6.32-21-generic             2.6.32-21.32                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic                       2.6.32.21.22                                    Generic Linux kernel image
ian@ian-desktop:~$ 

so if it will help how do i install it

---

### Post by dino99 on 2010-05-26
goto synaptic to select the packages: header and image

i386 for 32 bits
amd64 for 64 bits

pae kernel to use 4 gb or higher ram with 32 bits

---

### Post by cain071546 on 2010-05-26
its only got 1.5gigs of ram
So Wye is the pae kernel there?

---

### Post by cain071546 on 2010-05-26
hello.....?      any help would be cool.

---

### Post by dino99 on 2010-05-26
> **cain071546 said:**
> its only got 1.5gigs of ram
So Wye is the pae kernel there?

only for opened mind :P

---

### Post by cain071546 on 2010-05-26
> **dino99 said:**
> only for opened mind :P


ha ha ha ha ha... ***

---

### Post by cascade9 on 2010-05-26
> **cain071546 said:**
> its only got 1.5gigs of ram
So Wye is the pae kernel there?

PAE kernel is 'there' (in synaptic) becuase some people like to use it. I'd never bother, if you have 4GB of RAM then use 64bit IMO. Synaptic doesnt 'know' what kernels will work better than others in your machine. 

AFAIK,the generic kernel uses SMP. 

As for why your 2.0 seems to run faster thean the 2.6 (which is very odd, 2.0Ghz P4 are a LOT slower than a 2.6Ghz HT)- is it the same version of ubuntu? Done any modifications to the install on either machine?

---

### Post by 3rdalbum on 2010-05-26
Generic is the correct kernel to use, with or without PAE.

If your computer feels sluggish, you should be looking in userspace, not kernelspace. What I mean by that is: It's much more likely that you've got a program running that is eating up CPU power, thus causing the system to become slow. Find that program and kill it. The "top" command, or System Monitor, can help you there.

---

### Post by cain071546 on 2010-05-26
its a new install. i let the live cd install automatically i didn't touch any thing
ive install ubuntu on 5PCs with that disk, tried to use it on this and that's what i got

---

