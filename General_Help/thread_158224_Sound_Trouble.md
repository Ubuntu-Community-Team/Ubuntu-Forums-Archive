---
title: "Sound Trouble"
date: 2006-04-10
forum: General Help
---

### Post by jdm2 on 2006-04-10
I don't know any of the technical details right now but the person that is helping me get ubuntu 5.10 Breezy Badger install and set-up is having a trouble getting the sound workng.  I know the desktop enviroment is GNOME and it's version 5.10 of Ubuntu.  Can you help me out?  Thanks](*,)

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=jdm2]I don't know any of the technical details right now but the person that is helping me get ubuntu 5.10 Breezy Badger install and set-up is having a trouble getting the sound workng.  I know the desktop enviroment is GNOME and it's version 5.10 of Ubuntu.  Can you help me out?  Thanks](*,)[/QUOTE]
You have no sound at all ? Make sure that it is not muted.

---

### Post by jdm2 on 2006-04-10
That could be it but the person helping me is a sysadmin so I doubt that's the problem but who knows.  I will talk to him tomorrow and ask.  Thanks for the suggestion.

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=jdm2]That could be it but the person helping me is a sysadmin so I doubt that's the problem but who knows.  I will talk to him tomorrow and ask.  Thanks for the suggestion.[/QUOTE]
What kind of sound card do you have ? When I installed Breezy on my laptop, I didn't have any sound either. I fixed this by upgrading my kernel from 2.6.12-10-k7 to 2.16.6-ck3. I wrote a a guide on it but if you are really new to Ubuntu, then you shouldn't attempt it. Compiling kernels can be tricky :???:.

---

### Post by jdm2 on 2006-04-10
I don't know what type of card off top of my head and I'm new to ubuntu and linux.  All I know is it is the sound card that came with the hp system I got for xmas.

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=jdm2]I don't know what type of card off top of my head and I'm new to ubuntu and linux.  All I know is it is the sound card that came with the hp system I got for xmas.[/QUOTE]
type the following in terminal and post it here. This will show if Ubuntu is reconizing your sound card. Just copy and paste.

> lspci

---

### Post by jdm2 on 2006-04-11
I will tell him that and have him send me the result.  When I get them I will post them.  I was tld by this kid I know that there are different sound service in linux one is jack, one is oss, and the other is als I think.  He recommended the oss.  Got any tips on that for me?  Thanks

---

