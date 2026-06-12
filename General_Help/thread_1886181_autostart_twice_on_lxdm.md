---
title: "autostart twice on lxdm"
date: 2011-11-24
forum: General Help
---

### Post by ptrakk on 2011-11-24
i went to lxdm from gnome to run a minecraft/internet connection sharing/snort server with a gig of ram. i put a beep script in my ~/.config/autostart to tell when it is up and running. for some reason it executes twice. i believe it is traces of the old gnome coming to haunt me because i didn't purge it. 

I followed this advice [http://www.psychocats.net/ubuntu/purelxdemaverick](http://www.psychocats.net/ubuntu/purelxdemaverick)
i had to use 'aptitude --remove' instead of apt-get because of all the packages i didn't have installed. then 'apt-get install lubuntu-desktop'

i have read a bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=644628](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=644628) . i dont think it applies because i looked at the /etc/xdg/openbox/autostart.sh script and it refers to a /usr/lib/openbox/xdg-autostart which i dont even have!
:confused: :popcorn:
i cannot find the launcher for these applications and i want to disable one. anyhelp?

---

### Post by ptrakk on 2011-11-26
i found it. it is my 'tightvncserver'. it is definitely running everything twice. how do i fix this?

---

### Post by ptrakk on 2011-11-26
once more.. i figured it out. i simply removed 'startx' from my ~/.bash_profile

---

