---
title: "ubuntu black screen 11.04"
date: 2012-01-03
forum: General Help
---

### Post by yepimonfire on 2012-01-03
installed ubuntu 11.04 on an acer aspire 5732z and it WILL NOT BOOT. after the grub menu all i get is a black screen. i have spent the last two hours researching the issue and it seems like this is a big issue with 11.04. so far i have tried pressing "e" at the grub menu and replacing "quiet splash" with "nomodeset" but it always fails to boot when i do that. i cannot even get it to load.

i also saw a large thread on how to fix the issue but considering i'm new at using linux i don't understand half of the stuff in the thread. 

the computer has an integrated intel video card. any advice on how to get this working (keep in mind you're dealing with a noob here :P) would be greatly appreciated.

---

### Post by xc3RnbFO8P on 2012-01-03
> **yepimonfire said:**
> installed ubuntu 11.04 on an acer aspire 5732z and it WILL NOT BOOT. after the grub menu all i get is a black screen. i have spent the last two hours researching the issue and it seems like this is a big issue with 11.04. **so far i have tried pressing "e" at the grub menu and replacing "quiet splash" with "nomodeset"** but it always fails to boot when i do that. i cannot even get it to load.

i also saw a large thread on how to fix the issue but considering i'm new at using linux i don't understand half of the stuff in the thread. 

the computer has an integrated intel video card. any advice on how to get this working (keep in mind you're dealing with a noob here :P) would be greatly appreciated.

Dont replace, add it:
> quiet splash nomodeset
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1]("http://ubuntuforums.org/showpost.php?p=10069997&postcount=1")

---

### Post by yepimonfire on 2012-01-03
> **Ringi said:**
> Dont replace, add it:

[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1]("http://ubuntuforums.org/showpost.php?p=10069997&postcount=1")

all i get is a blinking cursor

---

### Post by xc3RnbFO8P on 2012-01-03
What is your computer spec?

---

### Post by yepimonfire on 2012-01-03
> **Ringi said:**
> What is your computer spec?

pentium dual core 2.22ghz
intel GMA
4gb DDR3 ram
250gb SATA HDD

its a notebook.

---

### Post by yepimonfire on 2012-01-03
also i tried using all of the methods in the thread you posted but none of them worked. still stuck with a black screen.

---

### Post by xc3RnbFO8P on 2012-01-03
Is it a Acer, HDMI or VGA output?

---

### Post by yepimonfire on 2012-01-03
> **Ringi said:**
> Is it a Acer, HDMI or VGA output?
i don't know...it's just a laptop with a screen that's connected.

there's no VGA or HDMI devices connected.

---

### Post by yepimonfire on 2012-01-03
anybody?

---

### Post by topsites on 2012-01-03
Yes, why are you using 11.04, the latest version is 11.10
I would start over.

---

### Post by yepimonfire on 2012-01-03
> **topsites said:**
> Yes, why are you using 11.04, the latest version is 11.10
I would start over.

i'm using 11.10 sorry

---

### Post by cbowman57 on 2012-01-03
Try this, add nomodeset & single to the kernel entry in grub to get into recovery mode, if that doesn't work try a different tty ctl+alt+f1 or f2, f3, if you get a terminal you can login & run an update & upgrade to see if that magically supplies a cure.

---

### Post by yepimonfire on 2012-01-03
> **cbowman57 said:**
> Try this, add nomodeset & single to the kernel entry in grub to get into recovery mode, if that doesn't work try a different tty ctl+alt+f1 or f2, f3, if you get a terminal you can login & run an update & upgrade to see if that magically supplies a cure.

could you please tell me exactly what to type into the box when i press "e" at grub.

---

### Post by cbowman57 on 2012-01-03
Just tag **nomodeset single** after quiet splash & see if it gets you to a recovery screen (fix file system & dpkg fix broken packages) .

Hopefully it will let you login that way.

---

### Post by xc3RnbFO8P on 2012-01-03
> could you please tell me exactly what to type into the box when i press "e" at grub.
Here is HowTo:
[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by agrgal on 2012-01-05
it could be solved by this post (sorry, spanish - both 11.04 & 11.10): [http://www.taringa.net/posts/linux/12439085/Solucionado-Problema-de-Pantalla-Aspire-5736z-Ubuntu-11_04.html]("http://www.taringa.net/posts/linux/12439085/Solucionado-Problema-de-Pantalla-Aspire-5736z-Ubuntu-11_04.html")

But now, my problem is, when saverscreen activates, that gets again black screen even though I've switched off saverscreens! No energy disconnection-features activated either.

Something else to do?

---

### Post by xc3RnbFO8P on 2012-01-05
> **agrgal said:**
> it could be solved by this post (sorry, spanish - both 11.04 & 11.10): [http://www.taringa.net/posts/linux/12439085/Solucionado-Problema-de-Pantalla-Aspire-5736z-Ubuntu-11_04.html]("http://www.taringa.net/posts/linux/12439085/Solucionado-Problema-de-Pantalla-Aspire-5736z-Ubuntu-11_04.html")

But now, my problem is, when saverscreen activates, that gets again black screen even though I've switched off saverscreens! No energy disconnection-features activated either.

Something else to do?

Here in English:
[http://translate.google.com/translate?hl=en&sl=es&u=http://www.taringa.net/posts/linux/12439085/Solucionado-Problema-de-Pantalla-Aspire-5736z-Ubuntu-11_04.html&ei=04YFT7yQKIOUOsnwsKUB&sa=X&oi=translate&ct=result&resnum=1&ved=0CCUQ7gEwAA&prev=/search%3Fq%3DSolucionado%2BProblema%2Bde%2BPantalla%2BAspire%2B5736z%2BUbuntu%2B11.04%26hl%3Den%26client%3Dubuntu%26hs%3DWjR%26channel%3Dfs%26prmd%3Dimvns]("http://translate.google.com/translate?hl=en&sl=es&u=http://www.taringa.net/posts/linux/12439085/Solucionado-Problema-de-Pantalla-Aspire-5736z-Ubuntu-11_04.html&ei=04YFT7yQKIOUOsnwsKUB&sa=X&oi=translate&ct=result&resnum=1&ved=0CCUQ7gEwAA&prev=/search%3Fq%3DSolucionado%2BProblema%2Bde%2BPantalla%2BAspire%2B5736z%2BUbuntu%2B11.04%26hl%3Den%26client%3Dubuntu%26hs%3DWjR%26channel%3Dfs%26prmd%3Dimvns")

---

