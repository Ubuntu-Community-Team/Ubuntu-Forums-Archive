---
title: "Frozen desktop gray Panels"
date: 2010-01-27
forum: General Help
---

### Post by sanukdo on 2010-01-27
I am really hoping this is an easy fix. Somehow, on my gnome desktop, my panels overlapped one another. I was dragging and dropping files into folders and unintentionally grabbed the smaller bar and dragged it over my larger application bar.

Now, when I rebooted, all I see is my desktop. I don't use icons so I have none of those. The panels are completely gray. every once in a while I will see my trash bin flashing. I am unable to right click the desktop and I am unable to use Alt+F2 for my term.

I can still use CTRL+ALT+ F1,F2,F3,F4... to get my non GUI terms. I have tried killall gnome-panel

still nothing.

This is a little... odd to me... a simple click renders an entire OS useless. I would really like to avoid uninstalling and reinstalling because that would just be something you would do with a microsoft product.

Any help would be SAAAWEEEET!

Edit: Everyone in a while I can right click the desktop and I get the provided menu but that does nothing for me. Also, my hard drive is constantly 'thinking' I am assuming it is stuck trying to complete the gnome environment settings... I am not sure. Oh, I have also tried removing gnome-panel and ubuntu-desktop and reinstalling those.

Ame thing happens in gnome failsafe mode

still nothing.....

---

### Post by ell02 on 2010-01-27
I would install xfce4 and xfce-goodies and pick that upon relog or reboot.Nice environment thats useable without installing a whole xubuntu. Someone smart will come along and fix you up i'm sure.

---

### Post by sanukdo on 2010-01-27
woooooooooo! I was sooooooo scared for a second.. I remembered an old command that I do not use much anymore lol...

rm... Yup 'rm' saved me from a life of pain and suffering...

anyhow... here is the solution

Log into xterm from boot menu and type:

rm -r ~/.gconf/apps/panel

restart

Granted I have to reset my bar settings but hey, I do not have to reinstall and update :)

---

### Post by llawwehttam on 2010-01-27
you could also have used 

```
gconftool-2 --recursive-unset
```

---

### Post by J V on 2010-01-27
pkill gnome-panels would have worked better :P

---

