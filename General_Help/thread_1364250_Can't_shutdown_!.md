---
title: "Can't shutdown !"
date: 2009-12-25
forum: General Help
---

### Post by alexplAnTe on 2009-12-25
Hi everyone ,

I can't shut down or reboot and when I click on Log Out, it just point me on a shell but I am still logged in.

The shut down and reboot button are grey and I can't click on them. The only way to shut down or reboot is to go in a terminal and type "sudo reboot" ...

How can I fix this ?


      [[IMG]http://img108.imagevenue.com/loc42/th_73684_Screenshot_122_42lo.png[/IMG]]("http://img108.imagevenue.com/img.php?image=73684_Screenshot_122_42lo.png")

---

### Post by bruno9779 on 2009-12-25
Whenever your computer or some program freezes

Click:

```
Ctrl+Alt+F1
```

This brings you to a tty session. Log in and :

```
sudo reboot
```

or, if you know which application is causing this:

```
sudo killall (name of application)
```

and

```
Ctrl+Alt+F7
```

to go back to the graphical session.


A lighter (and more correct) approach to reboot is restarting Xserver:

```
sudo service gdm stop
sudo service gdm start
```

(replace gdm with kde if you are on kubuntu)

---

### Post by khelben1979 on 2009-12-25
On Debian I just need to press: > ctrl + alt + delete to reboot the system (from the tty terminal). You can try if it works with Ubuntu as well.

---

### Post by bruno9779 on 2009-12-25
> **khelben1979 said:**
> On Debian I just need to press: ctrl+alt+del to reboot the system (from the tty terminal). You can try if it works with Ubuntu as well.

That has been disabled by default in ubuntu 9.10.

There are plenty of posts out there on how to activate it, but I like TTY better

EDIT: wait a minute, ctrl+alt+del in graphical session used to restart X in ubuntu, I am not aware of its behavior in TTY. Gotta try as soon as I get off work:(:(:(

---

### Post by blueridgedog on 2009-12-25
What happens if you try the following command in a terminal?

```
sudo /sbin/shutdown -h now
```

---

### Post by alexplAnTe on 2009-12-25
Yes I know how to shutdown with the terminal but it's the "GUI shutdown" ... you know that thing that let you choose between shut down , restart, suspend ... It won't let me shutdown , reboot ... because it's locked :confused:.

I don't have gdm , kdm, slim , xdm ... I just log in in the shell and then I fire startx .

---

### Post by Strongman332 on 2009-12-26
can you try to install a login mangier to try and fix this problem.

---

### Post by alexplAnTe on 2009-12-26
I installed gdm but it does not help ... so I uninstalled it.

I am sure that this is a permission problem ... I'll try to log in as root ... I'll be back in 1 minute :P

---

### Post by alexplAnTe on 2009-12-26
It DOES work in root so it's a permission problem . . . 

What do I need to change ? 
chmod something or maybe adding my user to the sudoer list ... I'll try it :)

---

### Post by alexplAnTe on 2009-12-26
Ok I added a screen shot :KS

---

### Post by Leppie on 2009-12-26
did you add this user to the sudoers?

---

### Post by alexplAnTe on 2009-12-28
Yes , I think so. But maybe I just did not added it correctly ... Can some one point me to a tutorial ?

---

### Post by john newbuntu on 2009-12-28
Could you please try one more thing here.  If you right click on the top panel and choose 'add to panel' and then choose "indicator applet session".  Now, does this provide you with the option to shutdown?

---

### Post by realzippy on 2009-12-28
[B]sudo chmod +s /sbin/shutdown
[/B]
gives "shutdown" superuser flag....

---

