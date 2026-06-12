---
title: "Instaling tar.bz software"
date: 2011-07-25
forum: General Help
---

### Post by friko16 on 2011-07-25
Hi.
Im new in ubuntu.
I want to instal aobe flash player. I downloaded a tar.bz file,after I extracted it I have this files:
libflashplayer.so and and some directories bin, lib , share.
How can I install this soft ? I googled I I didn't find info about what to do with this libflashplayer.so ?
Can anyone help ?

---

### Post by nothingspecial on 2011-07-25
> **friko16 said:**
> Hi.
Im new in ubuntu.
I want to instal aobe flash player.

install the ubuntu-restricted-extras package from the software center in your menu

---

### Post by friko16 on 2011-07-25
Ok I've alredy done this by synaptic, but im interested how to do this with this tar.bz described by me above ?

---

### Post by nothingspecial on 2011-07-25
Well, I'd remove flash before you do.

Doubleclick the file and choose to extract it to your home folder.

Have a look inside the extracted folder for some thing called README and the install instructions should be in there.

---

### Post by raja.genupula on 2011-07-25
[http://ubuntuforums.org/archive/index.php/t-49972.html](http://ubuntuforums.org/archive/index.php/t-49972.html)

---

### Post by Gyokuro on 2011-07-25
Hi,

copy the extracted libflashplayer.so to ~/.mozilla/plugins/ 

in case you do not have the plugins directory it's enough to make it via:

mkdir ~/.mozilla/plugins

restart firefox and you have flash :popcorn:

---

### Post by haqking on 2011-07-25
a tar is a compressed file, that needs extracting.

Its contents will vary from app to app.

there is usually a readme file enclosed with instructions such as compiling or installing.

in this particular case then as mentioned install the restrcited extras or if you really want to use the file you downloaded then you need to place the libflashplayer.so file into the plugins directory of your browser which is usually a hidden folder. example ~/.mozilla/plugins/

---

### Post by lovinglinux on 2011-07-25
If you are looking for installing Flash 11 Beta, then get Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard.

---

