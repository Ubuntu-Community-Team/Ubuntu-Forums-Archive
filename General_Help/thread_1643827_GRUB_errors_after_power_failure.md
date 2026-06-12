---
title: "GRUB errors after power failure"
date: 2010-12-12
forum: General Help
---

### Post by IBTB on 2010-12-12
Hi,

first let me tell what's happened:
A 66/12kV transformer blew up in my neighboorhood (not literally) causing a power failure where I have a old ubunto server stashed away.

I drove there to restart it when the power was back. Crossing my fingers the old machine had survived (it has survived failures before, so I didn't really worry so much about it). But when booting up it stalls allmost immediately with GRUB errors.


The computer has runned smoothly with few power failures and low load for .....yeah, who knows, since they still sold P4 prossessors and IDE harddrives! :P

Anyways, the first error I read (after getting a monitor for it) was something like this:
```
GRUB booting stage 1.5

ERROR 17
```
Witch I looked up on google and found 1000 different solutions and one page wich accually described the error itself ([http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html):
[quote=uruk.org]**17 : "Invalid device requested"**

This error is returned if a device string is recognizable but does not fall under the other device errors.[/quote]
I read more forum posts about the error and .....hmm, honestly I can't really remember what I read. But I tried to boot up without the HDD (there is only a single drive in the machine) and it was booting as expected, stopping because of no drive.
I then inserted the disk and booted again. This time it stopped on the GRUB loading page for a few seconds again, before it stopped with a new error. This time, error 18:
[quote=uruk.org]**18 : "Invalid or unsupported executable format"**

This error is returned if the kernel image boing loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).[/quote]

So, I've also read a few hours about this error, but haven't really found _the answer_! Only suggestions, and most of them are answers to people having multiboots (witch I don't).
Some of the tips are to reinstall GRUB on a new small partition. But I have mostly been using this as a web server, and my linux experience is abit limited. Been a few years since I had the time needed to sit down with it to learn.

So, to sum up:
Old machine -> worked flawlessly -> power failure -> GRUB errors -> In need of a sulution (a easily understood one preferably ;)).


I hope there is a way to link theese errors to the power failure and come up with a sulution that most probably will fix it! :)


Any help is appriciated greatly! 

//IB

---

### Post by IBTB on 2010-12-15
Hmmmm, after some "trying and failing" it finally booted.
What I saw in the BIOS was that the HDD stood as slave on the master IDE.
I didn't have any jumpers avalibe there and then so I just connected a CD-ROM as master and the error disapeared.

I doubt anyone else will ever occur anything like that, but just in case, now you know! :P

---

