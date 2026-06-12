---
title: "Blank Start Up Screen?"
date: 2012-01-10
forum: General Help
---

### Post by chrispche on 2012-01-10
Hi all,

How do I make the splash screen completely blank, no text, no splash screen. Total blackness is what I want. I'm using 11.10 Unity and I tried Start Up Manager with some success, but I still get the odd flash of text while booting. I just want it blank, black or whatever, I don't want anything to show.

Cheers in advance.

---

### Post by BlinkinCat on 2012-01-10
Hi,

I don't know the reason or answer for your question, but may I suggest that if you don't get your answer here that you try askubuntu - I have often received good results there. 

[http://askubuntu.com/](http://askubuntu.com/)

Cheers - :)

---

### Post by Krytarik on 2012-01-10
Setting "GRUB_CMDLINE_LINUX_DEFAULT" in "/etc/default/grub" to "quiet" should be sufficient enough.

/etc/default/grub:
```
[..]
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
[..]
```To edit that file, run:
```
gksudo gedit /etc/default/grub
```After saving the changes, update the GRUB config:
```
sudo update-grub
```More info reg. that:

[https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2)

Regards.

---

### Post by chrispche on 2012-01-11
Thank you for your responses.

---

### Post by chrispche on 2012-01-11
> **BlinkinCat said:**
> Hi,

I don't know the reason or answer for your question, but may I suggest that if you don't get your answer here that you try askubuntu - I have often received good results there. 

[http://askubuntu.com/](http://askubuntu.com/)

Cheers - :)

Do I have to have a reason? I prefer no info on booting up. It's just me, no reason. Cheers for that site by the way, very helpful. :D

---

### Post by BlinkinCat on 2012-01-11
> **chrispche said:**
> Do I have to have a reason? I prefer no info on booting up. It's just me, no reason. Cheers for that site by the way, very helpful. :D

Thanks very much for your kind words - they are very much appreciated - :P

---

### Post by Krytarik on 2012-01-11
> **chrispche said:**
> Do I have to have a reason? **I prefer no info on booting up. It's just me**, no reason.
In fact, *this* is the reason (the bold part). ;-)

---

