---
title: "Broke Compiz with dock"
date: 2006-06-27
forum: General Help
---

### Post by Kryten107 on 2006-06-27
I've been running Xgl / Compiz for over a month now with nice results, no problems at all. I recently changed to the quinn debs, still no problem and with a few upgraded / added plugins. This morning as I was browsing gconf I noticed dock and activated it, and it displayed but incorrectly, I believe some of the windows were black. I began closing windows (not sure why, it was 2 in the morning) and the dock shrank and shrank, eventually disappearing when there were no more windows left, and I ended up logging out to restart the session to see if it would fix it (maybe coming back with working mindows).  My Xsession would no longer start (and still no longer starts) giving the following error:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "devin"
/etc/gdm/Xsession: Beginning session setup...

```

Yes, that's the last line, "Beginning session setup...". I've googled and searched, but I haven't found that dock has killed anyone's session as badly as mine seems to have been killed, and I'm not sure what I need to do to fix it.

I have tried disabling dock in gconf and opening a new session, and I've also tried re-enabling it and opening a new session, always getting the same error, and I'm not sure what I can delete / edit / modify to try and get things back in order. Any advice is helpful, thanks!

---

### Post by no1wantdthisname on 2006-06-27
try
```
gconftool-2 --recursive-unset /apps/compiz
```
This will cause compiz to use the default settings.  If this doesn't work then I don't think your problem is with compiz.

---

### Post by matrooswolf on 2006-06-27
Did you update to the latest compiz from quinnstorm?  (0.0.13.0quinn4)
Dock and miniwin are disabled, and it looks a lot more stable ...
Maybe just updating could fix your problem?

---

### Post by Kryten107 on 2006-06-27
I tried no1wantdthisname's suggestion, and that didn't work. I've also tried downgrading my Compiz to the ubuntu depo version, and that hasn't done anything either.

> Did you update to the latest compiz from quinnstorm? (0.0.13.0quinn4)
Dock and miniwin are disabled, and it looks a lot more stable ...
Maybe just updating could fix your problem?

That's what I did last week, and yes, 0.0.13.0quinn4 worked very nicely. It was only when I activated dock that it broke, and now no matter what version of compiz I run it still won't start my default session.

I can't find the thread, but I remember seeing something about dock possibly breaking my .Xsession and that I should back it up...well, I didn't, but when I opened my .Xsession with gedit there's nothing to it, just loading screen 1 and activating all the compiz plugins (dock not included). I could load the backup Xsession, which is actually blank, and then it would possibly load but I think if I managed to activate compiz again it would break again.

I wish someone else had had this problem. o.O

---

### Post by Toufik on 2006-06-27
I've got nearly the same.

Compiz/XGL worked fine for one month. This morning, I decommented the compiz repositories in my apt/sources.list ([www.beerorkid.com](www.beerorkid.com) and xgl.compiz.info).  apt-get update & apt-get dist-upgrade.  It upgraded compiz, compiz-gnome, libglitz1, libglitz-glx1, libgl1-mesa,..

Then after rebooting, I'm unable to log in again in the XGL/Compiz session.  I get an error immediately.  It seems to compain about Xlib (the error is not very explicit and google gives nothing).  I tried different stuff (reinstalling, ...) but no way.  Finally, I've started over from the beginning and try glxinfo ---> direct rendering : No !!

I wonder what happens??  What could have disabled DRI?


PS:Dapper with gnome on a laptop with intel video card

---

### Post by matrooswolf on 2006-06-28
[QUOTE=Toufik]I've got nearly the same.

Compiz/XGL worked fine for one month. This morning, I decommented the compiz repositories in my apt/sources.list ([www.beerorkid.com](www.beerorkid.com) and xgl.compiz.info).  apt-get update & apt-get dist-upgrade.  It upgraded compiz, compiz-gnome, libglitz1, libglitz-glx1, libgl1-mesa,..
[/QUOTE]
Just a question, why did you decomment the compiz repo's from beerorkid?  Just wondering ...

---

### Post by Toufik on 2006-06-28
[QUOTE=matrooswolf]Just a question, why did you decomment the compiz repo's from beerorkid?  Just wondering ...[/QUOTE]
Just because when I've got something that work, I comment the backports and so one, to keep my system stable.  But after a new crash of compiz (miniwin I think), I decided to look for a new more stable version as I've heard about a new one, ... therefore I decomment it...  I wish I didn't

Well there is a new upgrade... gonna try it

EDIT : Yes! This is a new CVS and it works...

---

### Post by matrooswolf on 2006-06-28
Actually, I never use compiz when I work (only to show off at friends.  Compiz is extremely good at that ;)).  

I use metacity most of the time.  But I almost always work with Xgl, and then switch between metacity(work) and compiz (impress friends).

But I have the impression that compiz is more reliable with dock and miniwin disabled now ...

---

### Post by cowley on 2006-06-29
hi

i think you will find that dock and miniwin have been disabled as there is major issues with them - i wanted to use the dock thing and looking at the compiz site beforehand suggested that the newer releases of compiz have disabled these because of bugs.

simon

---

