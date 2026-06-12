---
title: "64-bit Ubuntu doesn't recognize all RAM"
date: 2010-04-11
forum: General Help
---

### Post by Danimoth on 2010-04-11
I have been using karmic since november and i just noticed >.<.
Ubuntu only recognizes 3.2GB of RAM. 

All i have found regarding this issue is regarding 32-bit Ubuntu which i already know won't recognize RAM above ~3GB, but i have been using 64-bit OS'es for a long time now because i usually have 4GB of RAM. 

BIOS sees 4GB of RAM without problems. 

Am i missing something?

---

### Post by audiomick on 2010-04-11
Have you got a video card that uses shared RAM? From what I have read, that is the most likely explanation.

---

### Post by Danimoth on 2010-04-11
I am on a desktop, which has a Geforce 9600 with its own RAM. 
I am not sure but I thought shared memory only applied to laptops, or am i wrong?

edit:
uname -a gives:
Linux alex-ubuntux64-1 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

and uname -m gives:
x86_64

---

### Post by audiomick on 2010-04-11
Ok, probably not the video card then (yes, I think there are cards for desktops with shared RAM).

I have seen a few threads regarding similar questions, but can't remember right now what the reasons for it were. Hang in there, I don't think anything is broken. ;)
Hopefully someone will turn up who knows a bit more about the subject.

---

### Post by Danimoth on 2010-04-11
Ok, thx for your help :).

---

### Post by egalvan on 2010-04-11
> **Danimoth said:**
> Ubuntu only recognizes 3.2GB of RAM.

Ubuntu recognizes whatever the BIOS says is left after the hardware takes it´s  share of RAM.
Video, audio, USB, FSB, BSB, etc...
then the software stuff...
pointers, caches, registers, etc
PAE, etc
all take RAM.

Thus and So...
Whatever is left after the **hardware** PROPERLY initializes is what the OS will get to use/see.

*(for clarity, I added the following, so future readers may better understand...)*

THEN, whatever is left after the **software** PROPERLY initializes is what the OS will report as "FREE"

> regarding 32-bit Ubuntu which i already know **won't recognize RAM above ~3GB**,

That statement is true only if the kernel AND the hardware do not utilize PAE,
otherwise, YES 32bit Linux CAN see/utilize more than 4GB of RAM

Any statement to the contrary is FUD...
And YES, I am using a 32Bit Ubuntu Hardy with 8GB RAM...
all 8GB seen and used.


>  but i have been using 64-bit OS'es for a long time now because i usually have 4GB of RAM. 

Great, but don´t blame 32Bit Linux, it´s been happily seeing more thatn 4GB for quite a spell...

> BIOS sees 4GB of RAM without problems. 
Am i missing something?

BIOS uses code to query RAM in order to ´see´ how much RAM exists. Then it starts handing out RAM to various...
see first part of this post.

---

### Post by Danimoth on 2010-04-12
> **egalvan said:**
> Ubuntu rcognizes whatever the BIOS says is left after the hardware takes it´s  share of RAM.
Video, audio, USB, FSB, BSB, etc...
then the sofware stuff...
pointers, caches, registers, etc
PAE, etc
all take RAM.

Whatever is left after the hardware PROPERLY initializes is what the OS will get to use/see.


Aha, then its not some kind of bug. I was used to seeing 4GB in Windows and didn't know this. 

> 
That statement is true only if the kernel AND the hardware do not utilize PAE,
otherwise, YES 32bit Linux CAN see/utilize more than 4GB of RAM

I also knew about PAE from the various threads i encountered just before posting this(before that i didn't know TBH), but i wanted to stress out that the OS was supposed to be able to see all RAM but it didn't, so the "problem" was somewhere else. 

Thank you for the thorough answer :).

---

