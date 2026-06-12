---
title: "escape from full screen app"
date: 2010-09-06
forum: General Help
---

### Post by tars_ac on 2010-09-06
Hello all,

I have a full screen program that I use to log in to work and control my work machine from home.  Unfortunately, once it is launched, I can't find any way to get out without closing the program, except for CTRL-ALT-F#, which doesn't really help since I can't get to my Gnome desktop from there as far as I can tell.  All other keyboard shortcuts that I know of in Ubuntu are getting captured by the application.  This is fine when I need to ALT-TAB in my work desktop, but I would really like to also be able to switch programs on my local desktop.  Apparently in Windows CTRL-ALT-DEL will work to get out, but that obviously doesn't work in Linux.  Does anyone know of any ways around this?

Thanks.

---

### Post by randallecook on 2010-09-08
Is it a fullscreen remote desktop (RDP) connection to a Windows machine? I use such a connection often and have found that ctrl-alt-enter takes you out of fullscreen mode. Try that.

Randall

---

### Post by tars_ac on 2010-09-11
Unfortunately, it's not the regular RDP connection, and CTRL-ALT-ENTER doesn't work (it opens the windows lock screen thing that gives access to the task manager, like ctrl alt delete).

---

### Post by hrickh on 2010-09-11
> **tars_ac said:**
> Hello all,

I have a full screen program that I use to log in to work and control my work machine from home.  Unfortunately, once it is launched, I can't find any way to get out without closing the program, except for CTRL-ALT-F#, which doesn't really help since I can't get to my Gnome desktop from there as far as I can tell.  All other keyboard shortcuts that I know of in Ubuntu are getting captured by the application.  This is fine when I need to ALT-TAB in my work desktop, but I would really like to also be able to switch programs on my local desktop.  Apparently in Windows CTRL-ALT-DEL will work to get out, but that obviously doesn't work in Linux.  Does anyone know of any ways around this?

Thanks.
Depends on what program you are using too, I suppose. If it's, for example, Virtualbox, the default hotkey combo to get out of full screen is Right cntl + F.

R.
==

---

### Post by tars_ac on 2010-09-11
It appears to be Citrix Metaframe, but I'm not really sure.  It looks heavily customized by my company.  As far as I can tell there *is* no hotkey to get out, at least according to the documentation provided by the company.  I guess what I'm looking for is something in the kernel or Gnome that can override an application to escape out.  For instance, since I can get to the terminal with CTRL-ALT-F1, is there something I can do to force gnome to minimize this app from the command line?  Or even to start a new Gnome session in another display?  It doesn't have to be perfect.

---

### Post by hrickh on 2010-09-11
> **tars_ac said:**
> It appears to be Citrix Metaframe, but I'm not really sure.  It looks heavily customized by my company.  As far as I can tell there *is* no hotkey to get out, at least according to the documentation provided by the company.  I guess what I'm looking for is something in the kernel or Gnome that can override an application to escape out.  For instance, since I can get to the terminal with CTRL-ALT-F1, is there something I can do to force gnome to minimize this app from the command line?  Or even to start a new Gnome session in another display?  It doesn't have to be perfect.
If you can get to a terminal, you should certainly be able to figure out what program is running. 

Worst case, you could always kill the application.

R.
==

---

### Post by tars_ac on 2010-09-13
Program is ICA Client (wfica).

The problem isn't that I can't kill it, the problem is that I don't want to kill it, I just want to get out of it.  If I kill it, then I have to go through the slow process of logging in and reconnecting.  I just want to get back to my desktop for a short period of time (like to change background music that's playing).

Thanks.

---

### Post by hrickh on 2010-09-13
Are you using this ICA client within a browser? Such as Firefox?

If you're using it in Firefox, try F11. that brings Firefox out of fullscreen.

Otherwise, I got nothin' (don't use ICA myself).

R.
==

---

### Post by tars_ac on 2010-09-13
No, it's a file downloaded by the browser and run separately.

---

