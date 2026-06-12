---
title: "Can't log in - log in window returns..."
date: 2010-02-27
forum: General Help
---

### Post by knutkja on 2010-02-27
Hi all,

I can't log in on my Acer Aspire One running Xubuntu 9.10. 

I restarted the computer half an hour ago, and when I fill in the log-in window, the pc spins a moment, and the log-in window comes back.

I can start up the KDE session, and have done so to post this.

Have any of you experienced something similar, and how can I fix it?

Thanks!

---

### Post by Brandon Williams on 2010-02-27
Attempt the xubuntu login. After it fails, login to KDE and examine ~/.xsession-errors.old. Does that file indicate any errors that could explain why the XFCE login is failing? If you're not sure, post the contents of that file so we can take a look.

---

### Post by knutkja on 2010-03-17
Sorry for my late reply! I have been logging on using [FONT=Courier New]xterm[/FONT] and starting the Xcfe desktop by typing [FONT=Courier New]startxfce4[/FONT].

I have checked the ~/.xsession-errors.old file, but it didn't make sense to me. It reads: 

[INDENT][FONT=Courier New]/etc/gdm/Xsession: Beginning session setup...[/FONT]
[FONT=Courier New] Setting IM through im-switch for locale=nb_NO.[/FONT]
[FONT=Courier New] Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.[/FONT]
[FONT=Courier New] xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":0.0"[/FONT]
[/INDENT] 
I hope it is some cure for this. Thanks!

---

### Post by kori.roxx on 2010-06-26
Hi, I have xubuntu 10.04 and I had this same problem.

I fixed it by switching my session on login to xterm, logged in, and in the window that popped up I typed this in the terminal (though you could do this in your tty sessions, or use KDE/Gnome):

 rm -rf ~/.config/xfce4/xfconf

Afterwards, I rebooted, and tried logging in again using the normal xfce session and it has been working fine since. :) Hope this helps!

---

### Post by Jordy_224 on 2010-11-26
Hey, 

   The same error has happened to me twice. After several attempts at clearing the home/user/.cache, updating video driver, re-setting the x-session options and ect , I settled for a reset of the desktop environment using... 

```
sudo tasksel 
```

---

