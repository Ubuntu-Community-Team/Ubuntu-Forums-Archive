---
title: "VGA drivers"
date: 2011-04-09
forum: General Help
---

### Post by L Style on 2011-04-09
I'm using ubuntu 10.04, I have ATI Radeon 7000 Rv100 VGA card I want this VGA card drivers for ubuntu. how can I installed it.

---

### Post by Krytarik on 2011-04-09
For this card, you can use the default open source driver, which is already included by the installCD, so you don't need to install it yourself. The proprietary driver doesn't support this card anymore.

If you want to try a more recent version of the open source driver, you can upgrade it through Xorg-Edgers' PPA:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If you need/want to downgrade again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```Greetings.

---

### Post by L Style on 2011-04-09
> **Krytarik said:**
> For this card, you can use the default open source driver, which is already included by the installCD, so you don't need to install it yourself. The proprietary driver doesn't support this card anymore.

If you want to try a more recent version of the open source driver, you can upgrade it through Xorg-Edgers' PPA:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If you need/want to downgrade again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```Greetings.
 Thnx friend

---

### Post by Hakunka-Matata on 2011-04-09
> **Krytarik said:**
> For this card, you can use the default open source driver, which is already included by the installCD, so you don't need to install it yourself. The proprietary driver doesn't support this card anymore.

If you want to try a more recent version of the open source driver, you can upgrade it through Xorg-Edgers' PPA:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If you need/want to downgrade again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```Greetings.

Sehr Geheerter symbol de Erde,  Ich mag Ihre avatar, Das finde Ich sehr klug:

Congratulations.

Andreas

---

### Post by Krytarik on 2011-04-09
> **Hakunka-Matata said:**
> Sehr Geheerter symbol de Erde,  Ich mag Ihre avatar, Das finde Ich sehr klug:

Congratulations.

Thanks! Actually, it's the logo of a mostly unknown rhythmic noise (industrial) band, but I associated it also with what you are referring to, and therefore it fits quite well, for now. ;-)

Also, thanks for using my native language, it's an honour!

---

### Post by Hakunka-Matata on 2011-04-11
It can be argued successfully that your native language has a more deserving ranking as the world/wide choice for scientific discussions than my tarnished (image) Englisch.  So you are most welcome and deserving of the hounour.

As you may habe vershectzt, Ich bin nicht Englisch.

---

