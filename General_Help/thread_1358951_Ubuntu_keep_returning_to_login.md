---
title: "Ubuntu keep returning to login"
date: 2009-12-19
forum: General Help
---

### Post by elliotn on 2009-12-19
How can I fix this. It gives me no error it just return to login screen.hw can I fix this

---

### Post by elliotn on 2009-12-19
anyone plz help needed

---

### Post by john newbuntu on 2009-12-19
Hit Ctrl+alt+F2 and Login. Check disk space using : df -h and see there is enough space.
Type:
sudo su
cd  /var/log/gdm
tail :0.log
tail -30 xsplash-user.log
tail -30 /var/log/Xorg.0.log
tail -30 /var/log/auth.log
See if you can spot anything strange in these last 4 logs.
To get back to gdm login, type exit and Ctrl+alt+F7

---

### Post by elliotn on 2009-12-19
Could it b my gfx as It started 2day when i put in a radeon 7000

---

### Post by elliotn on 2009-12-19
Any1 help a disperate guy plz

---

### Post by Chesamo on 2009-12-19
1. Start using proper English, you'll get a *much* better response
2. Do you have the latest video drivers for your card? (System > Administration > Hardware Drivers)

---

### Post by USB_NL on 2009-12-19
> **elliotn said:**
> How can I fix this. It gives me no error it just return to login screen.hw can I fix this

are you in a textinterface?

try:
startx

this wil start x windows (graphix interface of linux)

---

### Post by elliotn on 2009-12-19
> **USB_NL said:**
> are you in a textinterface?

try:
startx

this wil start x windows (graphix interface of linux)

I can get into gui interface but from nowhere it returns back to login screen, this started only now that i have installed a radeon 7000 gfx

---

### Post by elliotn on 2009-12-20
K its not the gfx as I have removed it but the problem continues and have reinstalled the os.

---

### Post by James78 on 2009-12-20
To me it sounds likely that X keeps crashing. Try checking your x session log in ~/.xsession-errors. You can easily get to this by running the failsafe terminal, and using a terminal editor like pico.

---

### Post by elliotn on 2009-12-20
> **James78 said:**
> To me it sounds likely that X keeps crashing. Try checking your x session log in ~/.xsession-errors. You can easily get to this by running the failsafe terminal, and using a terminal editor like pico.

Why would it fail, I have just reinstalled 9.04 and the problem still remain, a while ago 9.04 was working nicely with the same hadware. The only thing added now is just a 1gb ram

---

### Post by elliotn on 2009-12-20
Oh and now I also get this error

The greeter application appears to be crashing. attempting to use a different one


And also even FAILSAFE crashes and goes to login

---

### Post by James78 on 2009-12-20
If failsafe fails, I believe TTY should still work.

---

### Post by elliotn on 2009-12-20
And whats TTY

---

### Post by James78 on 2009-12-20
It's a system terminal, and there are more than 1. Ctrl + Alt + F1-F6, F8-F12 (Ubuntu usually uses TTY8 fyi)

---

### Post by elliotn on 2009-12-22
> **James78 said:**
> It's a system terminal, and there are more than 1. Ctrl + Alt + F1-F6, F8-F12 (Ubuntu usually uses TTY8 fyi)

Ok I can get into those terminal, now I need the commands to fix it

---

### Post by elliotn on 2009-12-23
Ok I give up.

---

### Post by elliotn on 2010-01-04
Ok am back, strange but I removed the sound card and problem is gone

---

