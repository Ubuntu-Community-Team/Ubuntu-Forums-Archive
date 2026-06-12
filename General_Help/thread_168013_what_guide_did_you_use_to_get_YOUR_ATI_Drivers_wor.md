---
title: "what guide did you use to get YOUR ATI Drivers working?"
date: 2006-04-29
forum: General Help
---

### Post by Dakaru on 2006-04-29
What guide did you use to get YOUR ATI Drivers working?

I have tried nearly every guide but they have all failed me, so I am wondering what guide you might have followed to get yours working because this is really bothering me i have yet to suceed at getting these drivers working. 


Please suply the link the the guide that you used so I can check if I tried that one and tell you what the problem was with it. Thank you.

---

### Post by bluevoodoo1 on 2006-04-29
Might want to post your video card model and/or system specs.... so someone can help you better.

---

### Post by Dakaru on 2006-04-29
ATI Radeon X700

---

### Post by srb715 on 2006-04-29
[This one.]("http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+glx")

Radeon x800PRO/9800PRO AGP

---

### Post by Dakaru on 2006-05-02
[QUOTE=srb715][This one.]("http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+glx")

Radeon x800PRO/9800PRO AGP[/QUOTE]
Did that.
But they run like piss. I get 1,800 in GLX Gears. Should get alot better than that.

---

### Post by Joshefson on 2006-05-03
I used method 2 and it works great for me.
Very good wiki.

[ATI Driver install Breezy and Dapper]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

Good luck ;)

---

### Post by Dakaru on 2006-05-04
[QUOTE=Joshefson]I used method 2 and it works great for me.
Very good wiki.

[ATI Driver install Breezy and Dapper]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

Good luck ;)[/QUOTE]

Tried that. 

I get an error that says incorrect kernal headers on this part.

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant a-i fglrx

---

### Post by djsroknrol on 2006-05-04
Hi Dakaru..

I searched the posts, and came up with the idea to use the "Radeon" driver..works fine for me..it supports your card...check this out [http://ubuntuforums.org/showthread.php?t=163982]("http://ubuntuforums.org/showthread.php?t=163982")..it's not exactly what you want, but it will give you a little direction possibly..good luck with it...

---

### Post by whiterussian on 2006-05-05
I got the same error for a bit, but with module assistant you can point it to your kernel headers. So ensure those are installed (try: apt-get install linux-headers, it wont work, but gives you a list, choose the appropriate). Then try something like this:

sudo module-assistant build,install fglrx -k /usr/src/linux-headers-2.6.15-22-386/

It works too!

alex@sex-cube:~$ glxgears -info
GL_RENDERER   = RADEON 9200 DDR Generic
GL_VERSION    = 1.3.1060 (X4.3.0-8.24.8)
GL_VENDOR     = ATI Technologies Inc.

*Goes to play ut2004 until his eyes bleed*

---

### Post by Jose Catre-Vandis on 2006-05-06
I used this one for my ATi 9550:

[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

Although I would like to know the best way to test "success"

---

