---
title: "Nautulis refuses to override the default."
date: 2011-12-08
forum: General Help
---

### Post by CinoxFellpyre on 2011-12-08
I am running on 11.04, using xubuntu.

I don't wanna get into WHY I am using xubuntu, but it involves a mishap  with compiz that i cannot recover now, so gnome is out of the question.

Anyways, I tried to use the ./defaultthunar script I was told to. I ran it once and got the confirmation that Thunar's default.

Problem is, I tried repeating it again to get my Nautulis back, and....well....

```
Changing to application launcher directory


Restoring backup files


Removing backup folder


Restoring Nautilus launcher

Removing 'local diversion of /usr/bin/nautilus to /usr/bin/nautilus.old'

Making Nautilus manage the desktop again

 17:59:14 up 14 min,  1 user,  load average: 0.38, 0.30, 0.32
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
cinoxfel tty7     :0               17:44   14:28   1:30   0.03s /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
root@cinoxfellpyre-Satellite-L305:/home/cinoxfellpyre#  /usr/share/themes/NOX/gtk-2.0/gtkrc:233: Murrine configuration option  "gradients" is no longer supported and will be ignored.

(nautilus:2994): EggSMClient-WARNING **: Failed to connect to the  session manager: Authentication Rejected, reason : None of the  authentication protocols specified are supported and host-based  authentication failed

**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init:  assertion failed: (connection->initialization_error == NULL)

```
I tried this normal, I tried this in root (against better judgement).  I'm still using xcfe, I just wanna be able to move my desktop icons like  I used to, and I really, REALLY hate thunar. :C

Maybe some assistance with this?

---

### Post by jerrrys on 2011-12-09
I haven't ran xubuntu since 10o4, in which I found that Nautilus did not play well as default.  The reason had something to due with gnome dependencies and I think I found that here:

 [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nautilus+xubuntu&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nautilus+xubuntu&sa=Search&cof=FORID:9)

maybe you will have better luck

---

### Post by CinoxFellpyre on 2011-12-09
....ya know I'm thinking.

Has anyone ever considered taking the good qualitie of xubuntu, and combining it with the good things of gnome?

I mean have like a comprimise between xubuntu and ubuntu. o.o

---

### Post by jerrrys on 2011-12-10
If you want to compare the two, why not just install them side by side and choose at log in.

---

