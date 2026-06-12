---
title: "Flash is not working"
date: 2010-11-14
forum: General Help
---

### Post by Isidorito on 2010-11-14
Hi, i erased compiz from my ubuntu, now, im having 2 problems

1- flash is not working: If you think in youtube, all the page charges, but the video is just a grey square.

2- I cant activate my "Extra" effects

I have:

GeForce 8400 GS (Recomended Drivers)
Firefox
Ubuntu MM


Thanks =)

---

### Post by x1a4 on 2010-11-16
Try to purge flash then install again.  
```
sudo apt-get purge adobe-flashplugin
sudo apt-get install adobe-flashplugin
```

---

### Post by hugomvera on 2010-11-16
[LEFT]I have the same problem. im pretty sure it is my cheap 30 dollar nvidia 8400gs card.  
with that card in use it would log me out of games and flash video. 


temporary solution
   deactivate your driver - hopefully your cpu will handle playing video on its own

[/LEFT]

---

### Post by hugomvera on 2010-11-16
real solution get a nicer graphics card.
I suggest getting an ATI ( opensource driverss!!)
 
i do not have this problem with my other ubuntu machine that has a nicer nvidia card.

---

### Post by Isidorito on 2010-11-24
srry but yhat is not the solution, whit my 8400gs i used to play flash games before this problem, and now, i can play WoW WoTLK full, so, the VGA its ok, i gonna try the purge =)

brb ;)


well ... it doesnt work :( i gonna keep looking

---

### Post by itang sanjana on 2010-11-24
```
dpkg -l *plugin*
``` see what missing .. HTH

---

### Post by Isidorito on 2010-11-24
> **itang sanjana said:**
> ```
dpkg -l *plugin*
``` see what missing .. HTH

> ayax@ayax:~$ dpkg -l adobe-flashplugin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nombre         Versión       Descripción
+++-==============-==============-============================================
un  adobe-flashplu <ninguna>      (no hay ninguna descripción disponible)
ayax@ayax:~$ 




I dont undersand... i have flash player installed, but it sais that

---

### Post by itang sanjana on 2010-11-24
Use wild-card *plugin* i.e. so you can trace down clearly and make sure you have java plugin too.

---

### Post by Isidorito on 2010-11-24
> **itang sanjana said:**
> Use wild-card *plugin* i.e. so you can trace down clearly and make sure you have java plugin too.

srry, but whats that? or how can i install it?

---

### Post by wojox on 2010-11-24
Use [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and you need compiz for extra-effects.

---

### Post by itang sanjana on 2010-11-24
I mean ```
dpkg -l *plugin*
``` instead of ```
dpkg -l adobe-flashplugin
``` :)

---

### Post by Isidorito on 2010-11-24
> **wojox said:**
> Use [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and you need compiz for extra-effects.

I have installed Flash Aid but i doesnt work.

i gonna install compiz and see what hapens

the info:

ayax@ayax:~$ dpkg -l *plugin*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nombre         Versión       Descripción
+++-==============-==============-============================================
un  adobe-flashplu <ninguna>      (no hay ninguna descripción disponible)
un  compiz-fusion- <ninguna>      (no hay ninguna descripción disponible)
un  compiz-fusion- <ninguna>      (no hay ninguna descripción disponible)
ii  compiz-plugins 1:0.8.6-0ubunt OpenGL window and compositing manager - plug
ii  evolution-plug 2.30.3-1ubuntu standard plugins for Evolution
un  evolution-plug <ninguna>      (no hay ninguna descripción disponible)
un  flashplugin    <ninguna>      (no hay ninguna descripción disponible)
ii  flashplugin-in 10.1.102.65ubu Adobe Flash Player plugin installer
ii  flashplugin-no 10.1.102.65ubu Adobe Flash Player plugin installer (transit
un  gstreamer0.10- <ninguna>      (no hay ninguna descripción disponible)
ii  gstreamer0.10- 0.10.20-1ubunt GStreamer plugins from the "bad" set
ii  gstreamer0.10- 0.10.20-1ubunt GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10- 0.10.30-2      GStreamer plugins from the "base" set
ii  gstreamer0.10- 0.10.30-2      GStreamer helper programs from the "base" se
un  gstreamer0.10- <ninguna>      (no hay ninguna descripción disponible)
ii  gstreamer0.10- 0.10.25-4ubunt GStreamer plugins from the "good" set
un  gstreamer0.10- <ninguna>      (no hay ninguna descripción disponible)
un  gstreamer0.10- <ninguna>      (no hay ninguna descripción disponible)
ii  gstreamer0.10- 0.10.16-1      GStreamer plugins from the "ugly" set
ii  gstreamer0.10- 0.10.16-1      GStreamer plugins from the "ugly" set (Multi
un  ia32-sun-java6 <ninguna>      (no hay ninguna descripción disponible)
un  icedtea-gcjweb <ninguna>      (no hay ninguna descripción disponible)
ii  icedtea6-plugi 6b20-1.9.1-1ub web browser plugin based on OpenJDK and Iced
un  konqueror-nspl <ninguna>      (no hay ninguna descripción disponible)
ii  libasound2-plu 1.0.23-1ubuntu ALSA library additional plugins
ii  libgstreamer-p 0.10.30-2      GStreamer libraries from the "base" set
ii  libmission-con 1:5.6.0-1      management daemon for Telepathy (library for
ii  libvisual-0.4- 0.4.0.dfsg.1-2 Audio visualization framework plugins
un  libvisual0.4-p <ninguna>      (no hay ninguna descripción disponible)
un  mozilla-plugin <ninguna>      (no hay ninguna descripción disponible)
un  pppdcapiplugin <ninguna>      (no hay ninguna descripción disponible)
ii  rhythmbox-plug 0.13.1-0ubuntu burning plugin for rhythmbox music player
un  rhythmbox-plug <ninguna>      (no hay ninguna descripción disponible)
ii  rhythmbox-plug 0.13.1-0ubuntu plugins for rhythmbox music player
un  seahorse-plugi <ninguna>      (no hay ninguna descripción disponible)
ii  sun-java6-plug 6.21dlj-0ubunt The Java(TM) Plug-in, Java SE 6
ii  totem-plugins  2.32.0-0ubuntu Plugins for the Totem media player
ii  vlc-plugin-not 1.1.4-1ubuntu1 LibNotify plugin for VLC
ii  vlc-plugin-pul 1.1.4-1ubuntu1 PulseAudio plugin for VLC


EDIT: I found that i can play ideos of youtube in other pages, for example the videos of this pages, but keeps not workunig in pages like Dinorpg (the log of this page doesnt succes if you flash plugin doesnt workm and i can log to it and play, but i cant saw the flash movies)

---

### Post by itang sanjana on 2010-11-24
```
ii flashplugin-in 10.1.102.65ubu Adobe Flash Player plugin installer
ii flashplugin-no 10.1.102.65ubu Adobe Flash Player plugin installer (transit
```

this could be your problem. You have 2 version of flash plugin. Purge both and than chose only one of them to install. I tend to flush plugin installer. HTH CMIIW

---

### Post by Isidorito on 2010-11-24
```
home/user# apt-get purge flashplugin-no 10.1.102.65ubu
E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
root@:/home/user# sudo dpkg --configure -a
Procesando disparadores para shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Procesando disparadores para man-db ...
Configurando libiodbc2 (3.52.6-4) ...
Procesando disparadores para hicolor-icon-theme ...
Configurando libqca2 (2.0.2-1ubuntu2) ...
Configurando soprano-daemon (2.5.2+dfsg.1-0ubuntu1) ...
Configurando libxine1-misc-plugins (1.1.18.1-4ubuntu4) ...
Configurando libstreams0 (0.7.2-1) ...
Configurando libqt4-svg (4:4.7.0-0ubuntu4) ...
Configurando libattica0 (0.1.4-1) ...
Configurando libthreadweaver4 (4:4.5.1-0ubuntu8) ...
Configurando libqt4-script (4:4.7.0-0ubuntu4) ...
Configurando libxine1-console (1.1.18.1-4ubuntu4) ...
Configurando libphonon4 (4:4.7.0really4.4.2-0ubuntu1) ...
Configurando kdebase-runtime-data (4:4.5.1-0ubuntu3.1) ...
Configurando libssh-4 (0.4.5-1) ...
Configurando kdelibs5-data (4:4.5.1-0ubuntu8) ...
Configurando libkdecore5 (4:4.5.1-0ubuntu8) ...
Configurando libclucene0ldbl (0.9.21b-2) ...
Configurando libxcb-shape0 (1.6-1) ...
Configurando libdbusmenu-qt2 (0.6.4-0ubuntu1) ...
Configurando libkdeui5 (4:4.5.1-0ubuntu8) ...
Configurando libkdnssd4 (4:4.5.1-0ubuntu8) ...
Configurando libkjsapi4 (4:4.5.1-0ubuntu8) ...
Configurando libsolid4 (4:4.5.1-0ubuntu8) ...
Configurando libkpty4 (4:4.5.1-0ubuntu8) ...
Configurando libsoprano4 (2.5.2+dfsg.1-0ubuntu1) ...
Configurando libstreamanalyzer0 (0.7.2-1) ...
Configurando libxine1-x (1.1.18.1-4ubuntu4) ...
Configurando libkdesu5 (4:4.5.1-0ubuntu8) ...
Configurando libnepomuk4 (4:4.5.1-0ubuntu8) ...
Configurando libkio5 (4:4.5.1-0ubuntu8) ...
Configurando libnepomukquery4a (4:4.5.1-0ubuntu8) ...
Configurando libknotifyconfig4 (4:4.5.1-0ubuntu8) ...
Configurando libknewstuff3-4 (4:4.5.1-0ubuntu8) ...
Configurando libkparts4 (4:4.5.1-0ubuntu8) ...
Configurando libktexteditor4 (4:4.5.1-0ubuntu8) ...
Configurando libkhtml5 (4:4.5.1-0ubuntu8) ...
Configurando libxine1 (1.1.18.1-4ubuntu4) ...
Configurando phonon-backend-xine (4:4.7.0really4.4.2-0ubuntu1) ...
Configurando libkfile4 (4:4.5.1-0ubuntu8) ...
Configurando libkmediaplayer4 (4:4.5.1-0ubuntu8) ...
Configurando libkutils4 (4:4.5.1-0ubuntu8) ...
Configurando libkatepartinterfaces4 (4:4.5.1-0ubuntu8) ...
Configurando phonon (4:4.7.0really4.4.2-0ubuntu1) ...
Configurando libqtwebkit4 (2.0.0-0ubuntu1) ...
Configurando libkdewebkit5 (4:4.5.1-0ubuntu8) ...
Configurando libplasma3 (4:4.5.1-0ubuntu8) ...
Procesando disparadores para libc-bin ...
ldconfig deferred processing now taking place
root@:/home/user# apt-get purge flashplugin-no 10.1.102.65ubu
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete flashplugin-no
E: No se ha podido localizar el paquete 10.1.102.65ubu
E: No se puede encontrar ningún paquete por la expresión de registro «10.1.102.65ubu»
root@:/home/user# apt-get purge flashplugin-in 10.1.102.65ubu
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete flashplugin-in
E: No se ha podido localizar el paquete 10.1.102.65ubu
E: No se puede encontrar ningún paquete por la expresión de registro «10.1.102.65ubu»
root@:/home/user# apt-get purge flashplugin-in 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete flashplugin-in
root@:/home/user# apt-get purge flashplugin-no
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete flashplugin-no
root@:/home/user# apt-get purge ii  flashplugin-in
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete flashplugin-in
root@:/home/user# apt-get purge flashplugin-in 10.1.102.65ubu
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete flashplugin-in
E: No se ha podido localizar el paquete 10.1.102.65ubu
E: No se puede encontrar ningún paquete por la expresión de registro «10.1.102.65ubu»

```

---

### Post by itang sanjana on 2010-11-24
OK, maximize your terminal. it is not flashplugin-no but flashplugin-nonfree ;) so here is the how:

purge both flash intalled
```
sudo apt-get purge flashplugin-nonfree flashplugin-installer
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

(re)install preferred flash plugin: flashplugin-installer i.e
```
sudo apt-get install flashplugin-installer
```

HTH CMIIW ..

---

### Post by Isidorito on 2010-11-24
It doesnt worked =(  I was looking around ind i found another guy who has the same problem but he sais its java the problem... i dont know :S

---

### Post by itang sanjana on 2010-11-25
> ii icedtea6-plugi 6b20-1.9.1-1ub web browser plugin based on OpenJDK and Iced
ii sun-java6-plug 6.21dlj-0ubunt The Java(TM) Plug-in, Java SE 6

yup I see you have 2 version of java plugin installed. Purge both, and then install one and only. HTH (dont forget to maximize the terminal ..)

---

### Post by Isidorito on 2010-11-25
> **itang sanjana said:**
> yup I see you have 2 version of java plugin installed. Purge both, and then install one and only. HTH (dont forget to maximize the terminal ..)


When you sais "maximaize the terminal" you says to work in full screen terminal?

And whats HTH or the oder apocope that you used?

Must go to work, back in a while (8 hours :P)

---

### Post by itang sanjana on 2010-11-25
> **Isidorito said:**
> When you sais "maximaize the terminal" you says to work in full screen terminal?
And whats HTH or the oder apocope that you used?
Must go to work, back in a while (8 hours :P)

maximize button, between minimize and close button, so you could read the package name clearly :) .. HTH (Hope This Helps)

---

