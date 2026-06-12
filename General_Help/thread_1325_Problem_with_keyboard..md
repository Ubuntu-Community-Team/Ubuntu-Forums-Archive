---
title: "Problem with keyboard."
date: 2004-10-20
forum: General Help
---

### Post by Neo40 on 2004-10-20
Hi,

Each time I start gnome there is a error message about my keybord. It says  brobably an error with  my Xserver. I played with "xf86config" to configure my k/b. (french-canadian).  This is the message I get:

Erreur lors de l'activation de la configuration XKB.
Probablement un problème interne au serveur X.

Données de version du serveur X :
The XFree86 Project, Inc
40300001
Vous utilisez XFree 4.3.0.
Il y a des problèmes connus avec les configurations XKB complexes.
Essayez d'utiliser une configuration plus simple ou utilisez une version plus récente de XFree.
Si vous rapportez cette situation comme une anomalie, veuillez inclure :
- Le résultat de xprop -root | grep XKB
- Le résultat de gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb


Here is  a part of my /etc/X11/XF86Config-4:

&lt;skip&gt;
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca_enhanced"
EndSection
&lt;skip&gt;


I can't find where is the problem?
Thanks for your help.

---

