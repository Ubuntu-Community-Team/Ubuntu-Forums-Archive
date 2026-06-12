---
title: "help I am logged off at loggin"
date: 2011-11-24
forum: General Help
---

### Post by elliotn on 2011-11-24
help people I have no access to my system now, it keeps login me off and takes me back to loggin screen, I input my password it goes in and second later it logs me off , I can't do a thing, am running 11.04

---

### Post by fdrake on 2011-11-24
are you sure your account isn't disabled because you have to much data on it? Try to login with the console (Ctrl+Alt+f1(f2,f3,..)) and see if you are able to login. Other wise use a live cd (or a root user )and navigate to your home dir and delete(move)some files. check also the file /etc/shadow ```
sudo less /etc/shadow
```and check the line containing your username:
if you see something like this
> username:[COLOR="Red"]_**!**_[/COLOR]j88d88gc873gd/:15200:0:99999:7::: 
with a "!" at the beginning of the hash , it means your account has been suspended for some reason.
if you don't see anything like this it means that there is an error in you conf files (possibly gnome).

ps: Do NOT post the content of you  /etc/shadow file in the forum!

---

### Post by tors on 2011-11-24
> **elliotn said:**
> help people I have no access to my system now, it keeps login me off and takes me back to loggin screen, I input my password it goes in and second later it logs me off , I can't do a thing, am running 11.04

Try CTRL+ALT + F1 and try to login on terminal.
(CTRL+ALT + F7 to get back)

---

### Post by sudodus on 2011-11-24
What happens if you try to start in recovery mode (from the grub menu)?

---

### Post by elliotn on 2011-11-24
solved, it looked like I didn't have space in my system, went to recovery and did clean

---

