---
title: "Which Kernel is using my ubuntu???"
date: 2012-06-05
forum: General Help
---

### Post by gurrunaki on 2012-06-05
Hi all, I'm looking install an antivirus in my pc and in my laptop, I like ESET NOD32, I sent a mail to them asking for information to see if is possible install the antivirus for my dual boot systems that are win xp 32 next to ubuntu 11.10 in my PC and Win 7 64 next to Ubuntu 12.04 in my laptop.
They told me that is possible if I know the kernel I'm using, this is what they sent to me: 

[COLOR=#1f497d][FONT=&quot]The ESET NOD32 is capable of protecting your PC from Internet and USB attacks.[/FONT][/COLOR]
 [COLOR=#1f497d][FONT=&quot]Smart Security is capable of protecting your PC as well but it has some features that you do not need.[/FONT][/COLOR]
 [COLOR=#1f497d][FONT=&quot] [/FONT][/COLOR]
[COLOR=#1f497d][FONT=&quot]If you want to install ESET to your Ubuntu systems you will have to check the kernel the are having.[/FONT][/COLOR]
 [COLOR=#1F497D][FONT=&quot]ESET can be installed to systems with kernel 2.4.x and 2.6.x[/FONT][/COLOR]

[COLOR=#1F497D][FONT=&quot][/FONT][/COLOR]
[COLOR=#1F497D][FONT=&quot]How can I find out the kernel are using my pcs?[/FONT][/COLOR]

[COLOR=#1F497D][FONT=&quot][/FONT][/COLOR]
[COLOR=#1f497d][FONT=&quot]Thanks in advance!!!
[/FONT][/COLOR]

---

### Post by texpat on 2012-06-05
Get a terminal and type
```
uname -r
```
The output should look something like this
```
user@host:~$ uname -r
2.6.32-41-generic
user@host:~$
```
which gives you the info you're after.

---

### Post by dino99 on 2012-06-05
why using linux if you still think windows ?

sudo apt-get install synaptic
sudo synaptic

look at : clamav, clamtk, ufw, gufw

---

### Post by gurrunaki on 2012-06-05
Thanks for your fast reply.

Texpat, now I now that in my pc I'm using 3.0 and in my laptop 3.2 I will ask to ESET if I can install the antivirus with this kernel.

Dino 99, I'm newbie in Linux, and I know I'm not clever enough and I don't have this key to push it and change your mind in seconds after many years under windows, anyway, thanks for your help and what you say I should look, is Chinese for me, but I will try learn it. For a person new in this system I think is not a big help what you wrote in your message, but if this system is just for professionals, just write it in the web from ubuntu for warn to the people interesting on it.

Cheers

---

### Post by 3rdalbum on 2012-06-05
There are currently no viruses that even work on Linux. The only reason you would need an anti-virus is if you want to check for Windows viruses.

If you're looking for an anti-virus program to keep your Ubuntu protected against virus infections, then you're looking for something completely unnecessary.

I believe Ubuntu 11.10 uses kernel 3.0, anyway.

But please don't make your computer slower by installing anti-virus software.

EDIT: I don't think what dino99 said was very helpful, either. They were actually suggesting that, if you want anti-virus, to try installing 'clamtk' from Ubuntu Software Center; but once again it's still not necessary, and it wasn't a very helpful way of saying it either.

---

### Post by texpat on 2012-06-05
Well, seing as

> If you want to install ESET to your Ubuntu systems you will have to check the kernel the are having.
ESET can be installed to systems with kernel 2.4.x and 2.6.x

you're probably out of luck.

If I understand correctly, you have one or several machines with Ubuntu and Windows in dual boot. This means that they run either Windows or Ubuntu at any one time.

For your Windows, you need an anti-virus. For Ubuntu, on the other hand, you don't, as has been pointed out by others. Also, from what you write it sounds like you are trying to install an AV for Windows and Ubuntu simultaneously. I'm pretty sure that cannot be done. You install on Windows and on Ubuntu separately. But, as said before, you don't need an AV in Ubuntu.

---

### Post by dino99 on 2012-06-05
> **gurrunaki said:**
> Thanks for your fast reply.

Texpat, now I now that in my pc I'm using 3.0 and in my laptop 3.2 I will ask to ESET if I can install the antivirus with this kernel.

Dino 99, I'm newbie in Linux, and I know I'm not clever enough and I don't have this key to push it and change your mind in seconds after many years under windows, anyway, thanks for your help and what you say I should look, is Chinese for me, but I will try learn it. For a person new in this system I think is not a big help what you wrote in your message, but if this system is just for professionals, just write it in the web from ubuntu for warn to the people interesting on it.

Cheers

no want to hurt you but glad to put some spice in your life :) virus is bill's feature , does not have that on linux.

---

### Post by gurrunaki on 2012-06-05
Cool guys, I understood, I think I will put the AV in win and not in Ubuntu, I just worry if I can get something from the USB memory or if I can get some intrusion meanwhile I'm surfing in internet under Ubuntu, I heard many things about botnets and stuff like that going around and I would love protect my system from all of this.

Hey dino, no prob, thanks for your answer, just the fact you spent time try solve my question is more than worthy for me, I really appreciate it.

Peace man.

---

