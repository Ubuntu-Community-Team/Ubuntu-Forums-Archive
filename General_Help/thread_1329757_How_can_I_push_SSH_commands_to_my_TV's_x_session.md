---
title: "How can I push SSH commands to my TV's x session?"
date: 2009-11-17
forum: General Help
---

### Post by shoeman22 on 2009-11-17
I'd like to be able to ssh into my htpc from my laptop and then launch gui apps directly on the plasma.

Is this possible and if so how do I do it?  I hate having to bust out vnc just so I can hit alt-f2 and run my command.

Thanks

---

### Post by laceration on 2009-11-17
here is a good ssh howto:
[http://blog.dotkam.com/2009/03/10/run-commands-remotely-via-ssh-with-no-password/](http://blog.dotkam.com/2009/03/10/run-commands-remotely-via-ssh-with-no-password/)

Though, that is an unconventional way to do it -- most people would be using a remote control;).  I'm curious, is there some reason you don't want to setup a remote control?

---

### Post by shoeman22 on 2009-11-17
Thanks for the link, but I don't think that is quite what I'm looking for.  I have SSH setup just fine on the HTPC and can connect ok from my laptop.  I just need to know how to, from my Putty SSH window from my laptop to the HTPC, fire commands that affect the X window on the TV.

Like for example, if I run ```
username@htpc:~$ xbmc
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Error: unable to open display
FEH.py: cannot connect to X server
```

But if I open vnc and fire up a terminal from inside of gnome, and type xbmc and enter it load's just fine.  I just want to emulate that functionality from my laptops putty ssh session.

Also, I am using a remote control as well, but I've had some flakiness issues with lirc and I'm still getting the kinks worked out so I have to hard kill stuff once and awhile and it'd be nice to be able to restart everything at the same time I'm killing things:)

---

### Post by laceration on 2009-11-17
Not a good answer, but I would say get rid of xbmc and use MPlayer;)

---

### Post by fluffman86 on 2009-11-17
Run "export DISPLAY=:0.0" before issuing your command, where 0.0 is your X session display.  So:

username@laptop:~$ ssh username@htpc
username@htpc:~$ export DISPLAY=:0.0
username@htpc:~$ xbmc &

The final & tell xbmc to run without logging to your current terminal.  Or, if you want to let it log to the terminal, you can check out byobu, which is installed by default in 9.10, and is a pretty kicking implementation of screen (basically terminal windowing).

---

