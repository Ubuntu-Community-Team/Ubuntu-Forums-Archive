---
title: "reinstaller sans cd?"
date: 2012-03-18
forum: General Help
---

### Post by jeanlucmalet on 2012-03-18
Bonjour,
suite à un ennui disque il apparaît que mon système est partiellement corrompu. Je me suis dit, "qu'à cela ne tienne, on va reinstaller tout les paquets..." 
un petit tour sous synaptic, sélection de tout ce qui est installer, choisir pour re-installation, et vogue la galère... sauf que je me suis aperçu que synaptique ne re-installait pas tout... donc je me suis dit ok, retour au bon vieux shell... "dpkg --get-selections \* | awk '{print $1}' | xargs -l1 apt-get install -y" ok tout se passe comme prévu... sauf que bon je ne peux que constater que rien n'a changé...
-toujours pas d'icônes sous nautilius
-convert de imagemagick continue de segfaulter...
-divers autres petits symptômes chiants...

je suis étonné qu'une distrib comme ubuntu ne sache pas s'autoréparer... car bon j'utilise d'autres distrib un peu moins "user friendly" et même avec un gros crash, réparer un système ne m'a jamais pris plus de 2j...

merci de vos aides, car là j'avoue que je suis dubitatif, pas envie de formater le disque et re-installer de zero...
JL

---

### Post by Elfy on 2012-03-18
Hi - this is an English speaking forum.

If you can post in English please do so - if not there is a French forum here 

[http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)

Other support options in French 

[http://www.ubuntu.com/support/community/locallanguage#french](http://www.ubuntu.com/support/community/locallanguage#french)

---

