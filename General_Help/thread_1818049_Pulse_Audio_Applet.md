---
title: "Pulse Audio Applet"
date: 2011-08-04
forum: General Help
---

### Post by nankura on 2011-08-04
Hey guys

ok basicly, i want to completely remove alsa. i dont know why but alsa just isnt good for me. i dont like it and i prefer pulseaudio

But im not fond of the alsa mixer tool. on linux mint 10 gnome i removed the tool and installed the pulse audio files and the pulse audio applet which showed down the bottom of the taskbar to the far right and booted with the operating system

i want that same setup in xubuntu but im not sure how to do it, everytime i go to remove alsa it wants to remove xubuntu-desktop completely

---

### Post by WhiteHorse on 2011-08-04
google apt-get remove

---

### Post by nankura on 2011-08-04
well i understand the command but im asking if theres a big risk if i run the removal and what exactly i need to remove and add to pulseaudio and the pulse audio applet

---

### Post by CatKiller on 2011-08-04
> **nankura said:**
> 
ok basicly, i want to completely remove alsa. i dont know why but alsa just isnt good for me. i dont like it and i prefer pulseaudio

No you don't. If you remove ALSA, PulseAudio won't work anyway.

---

### Post by .... on 2011-08-04
There is an xfce plugin that allows you to use gnome panel applets (package is called xfce4-xfapplet-plugin). Once you have that, you can add the gnome indicator to your panel and it should show the sound indicator.

Actually, I have the pulseaudio indicator in my (Debian) xfce panel and I don't even have that package installed. *shrug*

---

### Post by Jose Catre-Vandis on 2011-08-04
I have found that if I install the pulse audio volume control, it takes over from the default mixer / volume control

---

