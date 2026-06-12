---
title: "nautilus running, but not opening"
date: 2011-07-26
forum: General Help
---

### Post by u-noob-tu on 2011-07-26
i just turned my computer on a few minutes ago (turned it off due to a storm), and immediately noticed my desktop icons were gone. so i went to places>desktop, and nautilus failed (and continues to fail) to open. i simply see a waiting cursor and a window tab saying "opening Desktop", and nothing happens. i checked system monitor, and nautilus is running, and its not listed as being unresponsive. when running from the terminal, i get no errors or anything, it just doesnt run. i did see that when i turned on my computer, i got a splash screen saying it was checking my discs for errors, but it only took about 15 seconds and didnt find any errors. also, right clicking on my desktop doesnt do anything, either. not sure what happened.

---

### Post by u-noob-tu on 2011-07-27
BUMP I really don't want to have to reinstall because of this.

---

### Post by hakermania on 2011-07-27
Ok, all of us may have programs even more important than this, so please bump every 24 hours!

Try: nautilus -q in a terminal and **when it finish execution** try to open a nautilus window

---

### Post by u-noob-tu on 2011-07-27
sorry, just that it seems im missing half my computers functionality because of this. heres the terminal output: ```
ryan@ryan-Studio-1737:~$ nautilus -q

(nautilus:2843): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

``` seems like something is getting in the way of nautilus.

---

### Post by hakermania on 2011-07-27
> **u-noob-tu said:**
> sorry, just that it seems im missing half my computers functionality because of this. heres the terminal output: ```
ryan@ryan-Studio-1737:~$ nautilus -q

(nautilus:2843): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

``` seems like something is getting in the way of nautilus.

Hm, I don't know many things about dbus but I assume that something's wrong :P
Did you try rebooting?
Also, remember that you don't lose any of the functionality actually, anything can be done through the terminal as well (many times even better) ;)

---

### Post by u-noob-tu on 2011-07-27
> **hakermania said:**
> Hm, I don't know many things about dbus but I assume that something's wrong :P
Did you try rebooting?
Also, remember that you don't lose any of the functionality actually, anything can be done through the terminal as well (many times even better) ;)
yeah, im not sure what it could be, im no expert either. yes, there is the terminal, but its just so much more convenient to have a GUI.

---

### Post by hakermania on 2011-07-27
> **u-noob-tu said:**
> yeah, im not sure what it could be, im no expert either. yes, there is the terminal, but its just so much more convenient to have a GUI.

What about rebooting?

---

### Post by u-noob-tu on 2011-07-27
Tried it several times, no change. I'm just going to reinstall. I had a lot of junk programs on my computer anyway.

---

