---
title: "No sound..."
date: 2006-05-04
forum: General Help
---

### Post by elfois on 2006-05-04
Hi to everybody, it's newbie talking ;) 
I've a problem with the sound in ubuntu breezy that I don't have in the live version.
I mean, in the live version the sound it's ok, ubuntu recognizes the sound card very well, Intel Corp. 82801DB (ICH4) AC'97 Audio Controller, but in the install version it isn't... I don't understand why and I don't know what I should do.
Does someone have ideas?

Thank's in advance
Bye
Stefano

EDIT: please move this thread in the right forum, sorry for the inconvenience

---

### Post by Sef on 2006-05-04
Copy and paste the results of these two commands from the terminal:

Applications > Accessories > Terminal

1) cat /proc/asound/cards

2) sudo gedit /etc/modprobe.d/alsa base

---

