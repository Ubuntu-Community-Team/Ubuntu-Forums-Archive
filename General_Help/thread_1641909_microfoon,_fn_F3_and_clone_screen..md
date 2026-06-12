---
title: "microfoon, fn F3 and clone screen."
date: 2010-12-09
forum: General Help
---

### Post by dumble on 2010-12-09
He,

I got a Asus EeePC 1005PE
Installed Ubuntu Netbook Edition 10.10

Updated to latest BIOS file on asus support site.
Updated all available updates via Update Manager.


**Not working:**
[LIST]
[*]Build-in microphone. I installed skype, used the echotest. But I can not hear myself.
[*]I tried connecting the netbook to the telivision with VGA-cable. But when I click apply, my netbook starts flickiring for 10seconds. And then automaticly turns the second screen of again. (see screenshot). The options 'same image in all monitors' does work, but then I get strange resolutions.
[*]The function-key (fn F3), to turn off touchpad, is not working.
[*]No multi-touch support
[/LIST]

How can I fix these faults?

---

### Post by dumble on 2010-12-11
anyone?

---

### Post by dumble on 2010-12-12
I think I maybe found solutions, but the commands are not working because maybe there are in french? Found a whole page in french, including a fix for the mircrophone:

> Activer le microphone :

Exécuter la commande :

$ sudo aptitude install linux-backports-modules-alsa-maverick-generic

Puis installer :

$ sudo aptitude install pavucontrol

Une fois l'application installée, l'ouvrir (contrôle de volume pulse audio) et aller dans l'onglet « périphériques d'entrée », décocher « verrouiller les canaux entre eux », mettre un canal (le gauche pour moi) a 90% et l'autre a 10%. Fermer l'application. 
[COLOR="Blue"]
[SIZE="2"]Source: [http://hardware.guenmat.com/display/index.php?file=AsusSeashell.txt](http://hardware.guenmat.com/display/index.php?file=AsusSeashell.txt)[/SIZE][/COLOR]


Does anyone know a translation of these commands?

---

