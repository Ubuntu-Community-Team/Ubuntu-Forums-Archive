---
title: "Oneiric's Chromium has weird key behaviour"
date: 2011-10-23
forum: General Help
---

### Post by Fallen_Demon on 2011-10-23
I just upgraded to 11.10, and as I prefer Chromium's dev console have installed it. One thing that really annoys me, though, is that it seems to have silly new key behaviours. 

Whenever I have text selected or have an input highlighted in the page, I can't use the Ctrl-* shortcuts. Also, when I have an input selected, Ctrl-W will delete the last word.

Needless to say, this is a massive annoyance for me as I used them extensively and now have to go back to my mouse, click of any input or highlighting and then use the shortcut. Does anyone know how to turn this off?

---

### Post by Fallen_Demon on 2011-10-24
Forgive the double post and bump, but this feels like a rather elementary config problem. I've found that Firefox does exactly the same thing. When I have the URL input selected, it will not let me hit Ctrl-K to move across to the search box. Someone must know something about this, it seems so simple, but my GNOME configuration skills are not crash hot enough to be able to track it down myself

---

### Post by Fallen_Demon on 2011-10-24
Ok, now seriously, what the hell? Just had Gedit open and I couldn't Ctrl-F, it just scrolled across the goddamn page. Whoever made this change deserves to be shot, drawn and quartered for it

EDIT:

Found [https://bugs.launchpad.net/unity/+bug/849732](https://bugs.launchpad.net/unity/+bug/849732), will wait for the patch and then bitch and moan some more if it doesn't work

---

### Post by oldtimer7777 on 2011-10-24
Have you tried to install the latest Chromium build yet?

sudo add-apt-repository ppa:chromium-daily/ppa 
sudo apt-get update && sudo apt-get upgrade

---

### Post by Fallen_Demon on 2011-10-24
It's nothing to do with Chromium, I've found. If you look at the launchpad bug I posted, it's right across Gtk+3.0

---

