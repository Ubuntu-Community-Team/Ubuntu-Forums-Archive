---
title: "strange and difficult problem with sound on ubuntu 9.04 (problema extraño y dificil)"
date: 2009-09-18
forum: General Help
---

### Post by martin1717 on 2009-09-18
In English
some time that I have problems with sound on my Toshiba Satellite M55-S141 ATI sound card since installing Ubuntu 9.04. in the first stage all I heard was the sound branded (tatatatatata), then update alsa to version 1.0.20 and the problem is relief. Sometimes tore good, sometimes bad, and when pulled it after a while was branded. The problem is a little relief when I installed the latest version of alsa 1.0.21. Now always start well but after a while of use "tatatatata" and I restart the machine (reboot only alsa does not work). That is strange. It seems that after a while, "is filled or saturated with something, and that makes it tick sound. Stranger still is not enough to restart alsa only. This problem has me fed up and is the only reason that I can not recommend ubuntu. Help me please? Thanks  

En Español
hace tiempo que tengo problemas con el sonido en mi Toshiba satellite M55-S141 tarjeta de sonido ATI, desde que instale ubuntu 9.04. en la primera etapa lo único que escuchaba era el sonido tildado (tatatatatata), luego actualice alsa a la versión 1.0.20 y el problema se alivio. A veces arrancaba bien, a veces mal, y cuando arrancaba bien después de un tiempo se tildaba. El problema se alivio un poco mas cuando instalé la ultima versión de alsa 1.0.21. Ahora arranca siempre bien, pero después de un tiempo de uso "tatatatata" y debo reiniciar la maquina (reiniciar solo alsa no funciona). Por eso es extraño. Parece que después de un tiempo, "se llena o satura algo", y eso hace que se tilde el sonido. Más extraño aún es que no basta con reiniciar solo alsa. Este problema me tiene harto y es la única razón que me impide recomendar ubuntu. Me ayudan por favor? Gracias

---

### Post by Liolikas on 2009-09-18
For sure not everyone have same problem and this is specific to your audio card. Post model here if you do not know post output of ```
lspci
```

---

### Post by martin1717 on 2009-09-18
ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)

---

### Post by martin1717 on 2009-09-19
any idea? (ninguna idea?)

---

### Post by csi_guy on 2009-09-20
I also have the same card in my PC, I am unable to make it function in ANY linux distro.  I was however able to make the login sound work but that is it.  I am starting to wonder if it will just not work with Linux.

---

### Post by martin1717 on 2009-09-21
then back to windows? (vuelvo a windows entonces?)

---

### Post by P4man on 2009-09-21
try this:

```
sudo gedit /etc/modprobe.d/alsa-base.conf

```
add this line:

```
options snd-atiixp ac97_quirk=3
```

---

### Post by martin1717 on 2009-09-21
the problem remains the same. I think the problem is not alsa. Thanks for helping. (el problema sigue igual. me parece que el problema no es por alsa. gracias por ayudar)

---

### Post by martin1717 on 2009-09-22
when the sound stops working, I can't watch videos on youtube. strange? (cuando deja de funcionar el sonido, no puedo ver videos en youtube. raro no?)

---

### Post by martin1717 on 2009-09-24
Ubuntu needs to improve compatibility with hardware (ubuntu tiene que mejorar la compatibilidad con el hardware)

---

### Post by Kwnagi on 2009-10-01
Hi Martin, I have the exact same problem. The model of my lap is Toshiba Satellite L20 and my sound card is also ATI. Have you tried to follow the guide of markbuntu ?:

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

thats the next thing I am going to try.

Luck,

Kwnagi

---

### Post by Kwnagi on 2009-10-01
Tried the steps before the part for recording, didnt work for me. :(

---

