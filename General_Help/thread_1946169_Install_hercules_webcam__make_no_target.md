---
title: "Install hercules webcam : make no target"
date: 2012-03-24
forum: General Help
---

### Post by betsprite on 2012-03-24
HI all,

I have a problem to install my hercules webcam on ubuntu.

I have read this [link]("http://doc.ubuntu-fr.org/ov51x").

But when i tried to compile with a "make" with the latest version (1.5.9), i have the following message :

> *****@*******:~$ cd ov51x-jpeg-1.5.9
*******@******:~/ov51x-jpeg-1.5.9$ make
make: *** Pas de cibles. Arrêt.


"no target" apparently.

Have you any ideas ?

Thank you a lot :)

---

### Post by miegiel on 2012-03-24
I can't really help you, sorry, my french isn't good enough to read the howto.

I do have some comments though :D

Compiling stuff from source is a bit hard when you're new to ubuntu (or linux). Though the leap isn't great if you're a programmer, you might be better off finding a solution that doesn't require compiling stuff. Besides, considering more people probably have this camera, someone might have done the work already and compiled a *.deb* package to use.

**ps** Welcome to ubuntu forums.

---

### Post by betsprite on 2012-03-24
Thank you miegiel for your answer !

Yes i'm new to linux :p i try to find a .deb to avoid to compile because i didn't manage to do this.

But i don't know exactly what i'm looking for :s

i don't find a .deb package :s

If someone knows an interesting link it would be very nice :)

Ty !

---

### Post by Hubertt38 on 2012-04-27
Hi,

I have the same problem. I've tried to install my webcam using the same howto, and I'm stuck to the same point. What I did :

get my webcam version:
lsusb

install the headers
sudo apt-get install linux-headers-`uname -r`
then compiler[FONT=monospace]
[/FONT]sudo apt-get install gcc

then find the module, unzip it on my desktop, then go in that folder[FONT=monospace]
[/FONT]cd ov51x-jpeg-1.5.9

and the make command gives me this error:
make: *** Pas de cibles. Arrêt.

I'm running on Ubuntu 11.10 x64 with kernel 3.0.0-17-generic

It seems that some people can go through the installation, but with older kernel. And it seems that we have to perform the installation each time we update the kernel, that's maybe why we can't find any deb file.

Please can someone help ?

Thx

---

### Post by foooudre on 2012-04-30
hello friends
i have the same problem with my hercules blog webcam
same tuto and same error ;)

elle va me rendre fou cette webcam j'ai regler le probelem avant avec la 10.10 en installant les pilotes gspca trouver sur le site de moinejf.free.fr
mais la hélas ça ne marche plus et la LED de ma cam reste allumer tout le temps

---

