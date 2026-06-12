---
title: "Nothing makes ubuntu to use mp3"
date: 2006-03-28
forum: General Help
---

### Post by the_matador0 on 2006-03-28
I have installed all the codecs manualy, with automatrix and with easyubuntu 3 and nothing worked, the mp3 files just play but there is no sound, i love ubuntu mucho more than windows but i cant stand with and SO that dosent suports mp3's.

---

### Post by trent dillman on 2006-03-28
Is your sound muted? What player are you using? Did you enable the gnome sound fix in Automatix?

---

### Post by lupine_nickt on 2006-03-28
Do any other file-formats play with sound, or is it just mp3?

If I were you, I'd disable ESD, and then make sure that your sound program is setup with an ALSA driver. If you install XMMS to start with... I've had it work in situations when others wouldn't. 

You could always transcode everything to Ogg, I suppose... ;) 

xF,

...Nick

---

### Post by the_matador0 on 2006-03-28
Yeah, it pplays other formats, i tried with limewire, realplayer, totem etc... And nothing worked, in automatrix i selected everythinmg but i thing automatrix dosent works ok because it only insalled ok the amsn and the frostwire.
How do I disable ESD and whats that?

---

### Post by seppo on 2006-03-28
Jus to be sure. You have the mp3 codecs installed right?

> sudo apt-get install  gstreamer0.8-mad

---

### Post by the_matador0 on 2006-03-28
I only tried with the 7 codes manualy, by automatrix and by easy ubuntu, realy i dont know (being sarcastic)

---

### Post by the_matador0 on 2006-03-28
I tried with your code and this happened:
W: No se puede leer la lista de paquetes fuente [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No existe el fichero o el directorio)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

---

### Post by the_matador0 on 2006-03-28
(Is in Sapnish)

---

### Post by Buffalo Soldier on 2006-03-28
I don't understand Spanish, but judging from the error messages... I assume it says that you have not add the approriate/correct universe and multiverse repositories.

Have you tried [How do I add Universe and Multiverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse) and [How do I install multimedia codecs](http://help.ubuntu.com/starterguide/C/ch03.html#codecs) ?

---

### Post by the_matador0 on 2006-03-31
yes and yes, this sucks i cant stand an so that dosent supports mp3.
Ubuntu is full of errors, more than windows, sorry but im going to search another linux

---

### Post by seppo on 2006-03-31
sounds like a meatware error to me :-k

---

### Post by sbassett on 2006-03-31
[QUOTE=the_matador0]I tried with your code and this happened:
W: No se puede leer la lista de paquetes fuente [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No existe el fichero o el directorio)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas[/QUOTE]


Matadoro -

Are you sure there aren't any DNS issues and you are connected to the 'net.
If so, please try 
```
sudo dpkg --clear-avail dpkg --forget-old-unavail
```
Then try 
```
sudo apt-get update 
```
again. Then repeat seppo's suggestion again:
```
sudo apt-get install gstreamer0.8-mad
```

Let us know how you make out.

---

