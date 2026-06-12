---
title: "How to install the latest Flash Player?"
date: 2009-07-30
forum: General Help
---

### Post by Samsung570V on 2009-07-30
I am still a pretty new Ubuntu user, and the only problem I am having is that it can not play videos that are from the internet, such as videos from Youtube or Google Video. It says I need to download the latest version of Adobe Flashplayer, which is version 10. something. I tried downloading the Linux/Ubuntu version but for some reason it would not let me. 

Anyone have any tips for this? I am not sure how to use terminal, so it would be helpful if you could be specific about that if your response includes anything that needs the use of terminal.

---

### Post by aysiu on 2009-07-30
> **Samsung570V said:**
> I tried downloading the Linux/Ubuntu version but for some reason it would not let me. Adobe wouldn't let you download the Linux version? Or Ubuntu wouldn't let you install it? What was the error message you got?

Are you using 64-bit Ubuntu? Normal 32-bit? lpia kernel?

---

### Post by Samsung570V on 2009-07-30
I am pretty sure I have 32 bit Ubuntu. Is there some way to check that? I am trying to download Adobe Flash Player 10.0.32.18 Linux

---

### Post by Nburnes on 2009-07-30
In Teminal type

```
uname -a
```

Then post those for us please.

---

### Post by wojox on 2009-07-30
Open a terminal and paste this and hit enter:

```
uname -a
```

Copy and paste the results back and we'll tell you.

---

### Post by Samsung570V on 2009-07-30
usteven@SCREAMINGEAGLE:~$ uname -a
Linux SCREAMINGEAGLE 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
steven@SCREAMINGEAGLE:~$ 




yeah.... screaming eagle is the name of my computer. my friend made it that as a joke.

---

### Post by Samsung570V on 2009-07-30
I just installed Ubuntu 9.04 and need help with the flash player. I tried several other how-to's on the internet but could not get them to work. This is my info.

steven@SCREAMINGEAGLE:~$ uname -a
Linux SCREAMINGEAGLE 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

***my friend made the name of my computer screamingeagle as a joke.

---

### Post by credobyte on 2009-07-30
Have you tried installing restricted extras ?
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by QIII on 2009-07-30
Does your friend ride a Harley?

You can install the flashplugin-installer from Synaptic (respond back if you don't know how to do that) or through the terminal (same).

While there, remove swfdec and gnash since they will cause conflicts.

---

### Post by aysiu on 2009-07-30
Nope. No 64-bit.

Just download this file and double-click it:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

---

### Post by running_rabbit07 on 2009-07-30
> **Samsung570V said:**
> I am still a pretty new Ubuntu user, and the only problem I am having is that it can not play videos that are from the internet, such as videos from Youtube or Google Video. It says I need to download the latest version of Adobe Flashplayer, which is version 10. something. I tried downloading the Linux/Ubuntu version but for some reason it would not let me. 

Anyone have any tips for this? I am not sure how to use terminal, so it would be helpful if you could be specific about that if your response includes anything that needs the use of terminal.

The easiest way to get the Adobe flash player is to go to Myspace.com you will be offered the flash player if you don't have it installed.

---

### Post by steveneddy on 2009-07-31
> **aysiu said:**
> Nope. No 64-bit.

Just download this file and double-click it:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

I agree.

If you have a 32 bit Ubuntu OS then this is the way I would install it.

I just installed the 64 bit version and already notice the increased stability.

---

