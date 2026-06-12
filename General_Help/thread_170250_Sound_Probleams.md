---
title: "Sound Probleams"
date: 2006-05-04
forum: General Help
---

### Post by jdm2 on 2006-05-04
I haven't tested this yet but I will be doing it tonight or tommorrow.  The person who helped me get up and running said he couldn't get the sound to work.  Do you have any ideas what I should do or look for to make sure it works or get it to work.  Thanks

---

### Post by mjm115 on 2006-05-04
What type of soundcard do you have?  What does 

> 
lspci | grep audio


give you?

---

### Post by Sef on 2006-05-04
Application > Accessories > Terminal

Type in these two commands, (one at a time) then copy and past each one into here.

cat /proc/asound/cards

sudo gedit /etc/modprobe.d/alsa-base

---

### Post by jdm2 on 2006-05-04
Thanks I will do it when I get it tonight or tommorrow.

---

