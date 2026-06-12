---
title: "Killall gnome-panel kills gaim too"
date: 2006-02-09
forum: General Help
---

### Post by bluevoodoo1 on 2006-02-09
```
killall gnome-panel
```

...also kills gaim. Does this happen to anyone else? Is there another way to kill gnome-panel that will not kill gaim too?

---

### Post by WildTangent on 2006-02-10
[QUOTE=bluevoodoo1]```
killall gnome-panel
```

...also kills gaim. Does this happen to anyone else? Is there another way to kill gnome-panel that will not kill gaim too?[/QUOTE]
This happens to me as well, but it probably doesn't kill GAIM, probably just its system tray icon. Anyway...does it really matter that much?

-Wild

---

### Post by danhm on 2006-02-10
It's slightly annoying. Whenever I have to do something that requires me to kill the gnome panel, I just restart X (hit ctrl + alt + backspace), so I don't have to worry about panel icons going away.


I guess you could call that a work-around.

---

### Post by nanotube on 2006-02-10
i suppose that's more of a bug in gaim, probably not following some part of the gnome protocol for making sure that its applet is still displaying in the panel, rather than a bug in the panel... try filing that bug with gaim ([http://gaim.sf.net](http://gaim.sf.net)) - or even searching their bug database for it- maybe you will find a solution/workaround.

also, as to restarting x to fix this - it is probably much faster to just restart gaim, rather than all of X. (just find the gaim process in the system monitor, and kill it...)

---

### Post by bluevoodoo1 on 2006-02-10
[QUOTE=WildTangent]This happens to me as well, but it probably doesn't kill GAIM, probably just its system tray icon. Anyway...does it really matter that much?

-Wild[/QUOTE]


Well, I'm using Blackbox, and I don't have a system tray. So if there's something I need to use gnome-panel for I open it, and close it after. After I killall gnome-panel, I checked the command "top," no gaim running. enetered killall gaim "no process killed." So it does seem that it kills it. It's most annoying when I'm signed on to gaim....

EDIT: fixed typo

---

### Post by bluevoodoo1 on 2006-02-10
[QUOTE=nanotube]try filing that bug with gaim ([http://gaim.sf.net](http://gaim.sf.net)) - or even searching their bug database for it- maybe you will find a solution/workaround.
[/QUOTE]

[http://sourceforge.net/tracker/?group_id=235&atid=100235&func=detail&aid=1123184](http://sourceforge.net/tracker/?group_id=235&atid=100235&func=detail&aid=1123184)

There's been a bug post about it.

---

### Post by nanotube on 2006-02-10
hmm yea, that's the bug all right
but it seems to refer to gaim 1.1.4, and the bug is closed saying "it will be fixed in the next release". ubuntu breezy runs gaim 1.5.0, so it should be "fixed" already. so i guess question is, what version of gaim is the original poster running? if its 1.50 on breezy, bug needs to be reopened with gaim.

---

### Post by bluevoodoo1 on 2006-02-10
[QUOTE=nanotube]so i guess question is, what version of gaim is the original poster running? if its 1.50 on breezy, bug needs to be reopened with gaim.[/QUOTE]

Yes I'm running 1.50.

EDIT: found two more bug links citing this problem... 
[http://sourceforge.net/tracker/?group_id=235&atid=100235&func=detail&aid=1257433](http://sourceforge.net/tracker/?group_id=235&atid=100235&func=detail&aid=1257433)
[http://sourceforge.net/tracker/?group_id=235&atid=100235&func=detail&aid=1197320](http://sourceforge.net/tracker/?group_id=235&atid=100235&func=detail&aid=1197320)

perhaps 2.0 will solve this?

---

### Post by WildTangent on 2006-02-10
I just did a killall gnome-panel, and GAIM didn't die on me, but Beep Media Player did. Running GAIM v1.5.0

-Wild

---

### Post by bluevoodoo1 on 2006-02-10
here's some output... 

```

brian@ubuntu:~$ gaim &
[1] 7617
brian@ubuntu:~$ gnome-panel &
[2] 7618
brian@ubuntu:~$ killall gnome-panel
The program 'gaim' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1543 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[1]-  Exit 1                  gaim
[2]+  Terminated              gnome-panel

```

---

### Post by bluevoodoo1 on 2006-02-11
Found out that "killall fbpanel" also kills gaim... weird.

---

### Post by Mellon on 2006-02-17
amule goes too

---

### Post by erice on 2006-02-17
It's the same also with amule. Is there any way to keep running it when you restart the panel? Thank you.

---

### Post by bluevoodoo1 on 2006-02-24
[QUOTE=erice]It's the same also with amule. Is there any way to keep running it when you restart the panel? Thank you.[/QUOTE]

That is my question. (I haven't had any luck yet with the gnome-panel and gaim either...)

---

### Post by bluevoodoo1 on 2006-03-12
I've noticed with Blackbox (this probably won't work with GNOME!!!!!). If you have gnome-panel and gaim open and you go to Menu > Logout on the panel, it will close gnome-panel without killing gaim!

---

