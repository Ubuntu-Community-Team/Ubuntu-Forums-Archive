---
title: "vlc help"
date: 2006-01-20
forum: General Help
---

### Post by nominal on 2006-01-20
when  i go to the vlc site...it says i need to add a couple of lines to this sources.list

how do i do that? its a read only file...and yeah...
and even though im using ubuntu its ok that im using the d/l for debian right? cuz i think i read somewhere that ubuntu is kinda like debian....

:confused:

---

### Post by Iandefor on 2006-01-20
> when  i go to the vlc site...it says i need to add a couple of lines to this sources.list

how do i do that? its a read only file...and yeah...
and even though im using ubuntu its ok that im using the d/l for debian right? cuz i think i read somewhere that ubuntu is kinda like debian.... at the command line (Applications-->Accessories-->Terminal), enter the following to add a custom repository: ```
sudo "gedit /etc/apt/sources.list"
``` Sudo temporarily gives you super-user powers, and if you need to do something as root, you should use it instead. 

I think it'll install, but my suggestion would actually be to install it via [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563"). It's under Media Players.

---

### Post by nominal on 2006-01-20
k thanks for the help...i think i have a grasp on using 'sudo' now

---

### Post by nominal on 2006-01-20
actually it wont install straight from terminal and vlc, use automatix

---

### Post by Limulus on 2006-01-20
[QUOTE=nominal]when  i go to the vlc site...it says i need to add a couple of lines to this sources.list

how do i do that? its a read only file...and yeah...
and even though im using ubuntu its ok that im using the d/l for debian right? cuz i think i read somewhere that ubuntu is kinda like debian....

:confused:[/QUOTE]

Are you talking about [http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html) ?

Ubuntu is based on Debian, yes, but it has its own repositories to download from.

Follow the instructions on [my site](http://members.shaw.ca/Limulus/ubuntu.html#SynTer) to set up your sources.list file properly (just use the "Official Ubuntu Repositories" for now), then run Synaptic  (under System -> Administration), ignore the error and press reload, then install the "vlc" package (scroll down to "vlc", right-click it, Mark for installation, press the apply button).

Oh and avoid Automatix if you can help it ;)

---

### Post by Iandefor on 2006-01-20
[quote=Limulus]Oh and avoid Automatix if you can help it ;)[/quote] What's wrong with Automatix?

---

