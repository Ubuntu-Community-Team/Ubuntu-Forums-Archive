---
title: "How to config ubuntu not auto start gnome at startup?"
date: 2009-09-07
forum: General Help
---

### Post by cpthk on 2009-09-07
I have ubuntu desktop version. How do I config ubuntu not to start gnome at startup? I would like to start gnome when I need it, other than that, I only want command line. After I config that, how do I start gnome?

Thanks.

---

### Post by nothingspecial on 2009-09-08
If you want a way of starting gnome aswell you would be better of just stopping it after you have logged on.
```

sudo /etc/init.d/gdm stop
```

```
sudo /etc/init.d/gdm start
```

You could remove gdm from the start up scripts entirely but then, although not a problem, starting gnome would be more involved.

There may be an easier way.

---

### Post by wojox on 2009-09-08
How about just loading gnome and then Ctrl + Alt + F2 for a terminal

Ctrl + Alt + F7 back to gnome

---

### Post by sharath0007 on 2009-09-08
> **cpthk said:**
> I have ubuntu desktop version. How do I config ubuntu not to start gnome at startup? I would like to start gnome when I need it, other than that, I only want command line. After I config that, how do I start gnome?

Thanks.
hey, u can simply switch b/w cli and the gui by pressing ctrl+alt+(f2 to f6 ) then return back by pressing ctrl+alt+f7. 
When Linux starts up, it enters into what is referred to as a run level or system state.
Typically, a system set to start at run level 5 boots to a graphical login prompt. A system
set to run level 3 boots to a text prompt. The run level is set by the "initdefault" line in the /etc/
inittab &#64257;le. Change the number on the "initdefault" line as you please between 3 and 5. Don&#8217;t use
any other number unless you know what you are doing. Never use 0 or 6; those numbers are used to
shut down and reboot the system, respectively.

---

### Post by c9-3Rr0r on 2009-09-08
Simply change names of scripts in /etc/rc*.d/ (based on in witch mode you want to not start gdm). Every thing is described in README file (/etc/rc*.d/README)

Then if you want start gdm 
```

sudo startx

```

Also i think that removing xinit package should stop gdm to not load during the boot but i'm not sure about that u can check it by yourself.

---

### Post by cpthk on 2009-09-08
The thing I don't want it to start is because I want this machine to run as a server. But I still need the browser sometimes, so I don't want to completely remove it. I understand I could do ctrl+alt+f1~f6, but gnome is still running, which still waste my machine memory.

---

### Post by scrooge_74 on 2009-09-08
then dont install gnome, install another window manager or a lighter desktop and then remove gdm so it wont go into GUI it will start and drop you in a terminal so you can put your user and pass.

Then if you really want to start something you could just do startxfce4 and you will have a desktop

---

