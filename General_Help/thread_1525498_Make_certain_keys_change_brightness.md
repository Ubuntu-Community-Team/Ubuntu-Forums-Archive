---
title: "Make certain keys change brightness"
date: 2010-07-06
forum: General Help
---

### Post by alem189 on 2010-07-06
Hi, I have a simple question: I want to set fn + Up or Down Arrow to change the brightness of the screen, instead of fn + F4 and F5. However, I don't know the command to do that, and I can't find it in Keyboard Shortcuts. I've seen something about editing a file in /var, but that requires root permissions, and I'm pretty sure there must be a simpler answer... can anyone help me?

---

### Post by alem189 on 2010-07-06
*bump*

There's got to be some way...

---

### Post by Firedrake445 on 2010-07-06
In System>Prefrences>Keyboard Shortcuts their may be something their that you can set to make that key combo increase/decrease brightness.

---

### Post by alem189 on 2010-07-07
> In System>Prefrences>Keyboard Shortcuts their may be something their that you can set to make that key combo increase/decrease brightness.
I am absolutely sure that there is nothing related to changing brightness in the keyboard shortcuts dialog, as I said before.

---

### Post by alem189 on 2010-07-08
*bump*

---

### Post by jkid on 2010-07-08
ifu go in in terminal....to have full permision....type sudo -su

---

### Post by alem189 on 2010-07-08
> **jkid said:**
> ifu go in in terminal....to have full permision....type sudo -su

Yes, but that won't help in a script... and anyway, I don't want to be asked for a password every time I change the brightness.

---

### Post by alem189 on 2010-07-11
*bump*

---

### Post by alem189 on 2010-07-14
*bump*

---

### Post by alem189 on 2010-07-19
bump, again

---

### Post by simosx on 2010-07-21
/etc/udev/rules.d/README

---

### Post by alem189 on 2010-07-29
> **simosx said:**
> /etc/udev/rules.d/README

Hmm, I'm not sure what to do here... I've tried looking at some of the rules, going to the /lib/udev directories, searching on the Web, looking at the keymap.rules... I'm not sure how to bind a key here. Am I missing something?

---

### Post by alem189 on 2010-08-08
Any ideas? At all?

---

### Post by alem189 on 2010-08-11
How does the operating system communicate with the hardware to do this kind of stuff?
Is there any way I could change something at that level?

---

### Post by alem189 on 2010-08-24
Nevermind, I found a command:
```
xbacklight -inc/dec 10
```

---

