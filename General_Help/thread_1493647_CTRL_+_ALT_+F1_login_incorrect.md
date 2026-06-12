---
title: "CTRL + ALT +F1 login incorrect"
date: 2010-05-26
forum: General Help
---

### Post by Zireth ZH on 2010-05-26
Everytime a fullscreen game freezes i cant close it.. when i press ctrl alt f1 it asks me for login... i type in for example ubuntu which i guess it should be my user login, i type in my password but it sais login incorrect.... 

 im new to kill command but i learned how to do this... but from a terminal in the desktop...


Help please...

---

### Post by Zireth ZH on 2010-05-27
bump

---

### Post by VeeDubb on 2010-05-27
Your login name shouldn't be ubuntu unless that's the user name you set up for yourself.

It should be the same login information you use to log into the desktop.

---

### Post by maddox on 2010-05-30
Same problem here!! And same problem with sudo. But its very ramdom, eventualy it works after a couple of login attempts

maddox@MyBOX:~$ sudo synaptic 
[sudo] password for maddox: 
Sorry, try again.
[sudo] password for maddox: 
Sorry, try again.
[sudo] password for maddox:

---

### Post by Nythain on 2010-05-30
possibly misstyping your password??? without seeing it, it can be a bit tricky, i fubar my password about 1 out of every 5 tries

---

### Post by JustinR on 2010-05-30
Thats odd. All I usually do if a game of mine freezes, (because I'm not running any other programs), I press CTRL + ALT + BACKSPACE to kill the X server and log back in.

It works all of the time for me because Ubuntu itself has never crashed or froze on me.

You have to enable the shortcut under System > Preferences > Keyboard > Layouts then click the Options button.

---

### Post by km0r3 on 2010-05-30
> **Zireth ZH said:**
> Everytime a fullscreen game freezes i cant close it.. when i press ctrl alt f1 it asks me for login... i type in for example ubuntu which i guess it should be my user login, i type in my password but it sais login incorrect.... 

 im new to kill command but i learned how to do this... but from a terminal in the desktop...


Help please...

Are you sure you have the same [locale]("http://en.wikipedia.org/wiki/Locale") setting in your tty as you have in your gdm session? This may cause that your keyboard layout is different in the tty which causes that you unintentionally type the wrong password.

---

### Post by maddox on 2010-05-30
> **Nythain said:**
> possibly misstyping your password??? without seeing it, it can be a bit tricky, i fubar my password about 1 out of every 5 tries

I dont think so, because it happens quite a lot. And the keyboard is working fine.

I Have no ideia whats wrong with it.... its annoying

But there are other problems:


a) VTy´s do not work at start, if i go CTRL+ALT+F1 to F12 i get a black screen 

b) "sudo runlevel" returns "unknown"

c) "sudo telinit 2"  gets the VT working back again

---

### Post by hetemeleci on 2010-08-12
I have same problem.

but when I am trying to type my password from numpad it says "login incorrect".  but if I use other digit number keys to type password everything is success and it is login.

I think ctrl+alt+f1 doesnt work with my numpad.

Anyone has any idea about how to ctrl+alt+f1 recognise numpad.

---

### Post by WorMzy on 2010-08-12
Make sure that your numlock is enabled in the TTY. I don't think it is by default (it doesn't matter whether it's enabled in X, each TTY has it's own "is numlock on" value)

---

