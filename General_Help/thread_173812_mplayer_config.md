---
title: "mplayer config"
date: 2006-05-10
forum: General Help
---

### Post by blackjack6.21.91 on 2006-05-10
is there a way to configure mplayer so that when you maxamize mplayer it stretches the video (for fullscreen)?

thanks for the help in advance.
and if i'm not being clear just tell me

blackjack

---

### Post by ZylGadis on 2006-05-10
There is an option in the mplayer config file, /etc/mplayer/mplayer.conf - edit it and look through the options. Unfortunately I have forgotten what the option was exactly (I think it was zoom=yes), but you should find it after playing a bit with them. If your computer starts stuttering after you go fullscreen, changing the driver to vo=x11 might help, too.

---

### Post by blackjack6.21.91 on 2006-05-11
thanks alot

i've been wanting to be able to do that for a long time

---

### Post by nanotube on 2006-05-11
if you jsut change your driver to xv from x11, your problems will be solved (and your performance improved, to boot). 
to see more detail about this, click the first link in my sig, and find the section on configuring mplayer (or just search for "xv" a couple of times)

---

