---
title: "command for logout"
date: 2009-06-28
forum: General Help
---

### Post by oakdeveloper on 2009-06-28
Hi,

i am able to shutdown or restart my computer from the command line. Is there a command for logging out from the current session?

Thanks & Regards,
Babu

---

### Post by utnubuuser on 2009-06-28
read: > [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)ctrl+alt+F1 also gets you to a login screen. F7 will return you to xsession.

At the prompt, > logoutends the current user's session and returns a login prompt.  I don't think this applies to xsessions though.

but then you probably knew that...

---

### Post by kerry_s on 2009-06-28
> **oakdeveloper said:**
> Hi,

i am able to shutdown or restart my computer from the command line. Is there a command for logging out from the current session?

Thanks & Regards,
Babu

current session of what?

---

### Post by geirha on 2009-06-28
```
gnome-session-save --kill --silent
```

---

### Post by utnubuuser on 2009-06-28
xsession ( graphical session).  If you're talking about just working in a terminal environment without any graphical session in progress, "logout" returns you to a login prompt.

---

### Post by ~sHyLoCk~ on 2009-06-28
> **geirha said:**
> ```
gnome-session-save --kill --silent
```

This is how you do it. 
Also, 'logout' doesn't work from gnome-terminal, you may wanna edit your bash file do this:~
```
sudo gedit ~/.bashrc
```
and then put
```
alias logout='gnome-session-save --kill --silent'
```
Save and exit. And you may need to close your terminal and open it to make changes effective.
So next time you don't need to type that long command just type logout.

---

### Post by oakdeveloper on 2009-06-28
Thanks to all! I forgot to mention GNOME session. I have the answer now though. Thanks again!

---

### Post by colau on 2009-06-28
> **geirha said:**
> ```
gnome-session-save --kill --silent
```
+1
I was searching this.

---

### Post by led_belly on 2009-12-17
.

---

### Post by rpremuz on 2009-12-18
> **led_belly said:**
> Use --logout or --logout-dialog moving forward.

man gnome-save-session

Actually,

```
man gnome-session-save
```

(led_belly, you'd better do a copy-paste of a command you tried in a terminal window than type it from your memory as you may mistype something)

-- rpr.

---

### Post by geirha on 2009-12-21
Indeed, though in Ubuntu 8.04, it does not accept --logout, but in all newer releases, --kill and --silent are deprecated. So to sum up.

```

# Ubuntu 8.04
gnome-session-save --kill --silent
# Ubuntu 8.10, 9.04 and 9.10
gnome-session-save --logout

```

---

