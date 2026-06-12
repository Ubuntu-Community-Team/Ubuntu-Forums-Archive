---
title: "crontab X ACL"
date: 2009-11-03
forum: General Help
---

### Post by r-mo on 2009-11-03
I'm trying to set my computer to play my music from amarok as an alarm call.  I have the following line in my crontab.

50 06 * * 1-5 export DISPLAY=:0 && /usr/bin/amarok -p

This didn't work, syslog said the command ran but nothing happened. I looked at the documentation [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) and it say in Karmic you have to enable X ACL for localhost to connect to for GUI applications to work.  So I did what it says 

xhost +local:
xhost

and tested the crontab.  It works.  I turn my computer off and it wakes up this morning but it seems to have forgotten the ACL setting and my alarm doesn't go off.  

I guess that it's rebooting that caused the problem, is there a way to make this setting persist between reboots?

---

### Post by diesch on 2009-11-03
Use

```
DISPLAY=:0 XAUTHORITY=~/.Xauthority /usr/bin/amarok -p
```

instead of 

```
export DISPLAY=:0 && /usr/bin/amarok -p
```

XAUTHORITY=~/.Xauthority tells the program to get X credentials from the file ~/.Xauthority so you don't need to play with xhost.


"xhost +local" can cause security problems as it gives every program running on your computer full access to your X display - which usually means full access to your account.

---

### Post by r-mo on 2009-11-03
Thanks for the reply.  I'll test it out tonight and update the documentation if it all works :)

Cheers

---

### Post by r-mo on 2009-11-05
Still haven't got this to work :(

Tried with

```
env DISPLAY=:0 && env XAUTHORITY=~/.Xauthority && /usr/bin/amarok -p
```

also tried the /home/user instead of ~ but couldn't get it to run.  The cmd appears in syslog but nothing happens

---

### Post by diesch on 2009-11-05
Why don't you try
```
DISPLAY=:0 XAUTHORITY=~/.Xauthority /usr/bin/amarok -p
```

---

### Post by r-mo on 2009-11-06
Sorry, I should have mentioned I did try that as well.  It didn't work either.  Thought you'd just omitted the &&'s because the command didn't make much sense as it was.

---

### Post by diesch on 2009-11-06
> **r-mo said:**
> Sorry, I should have mentioned I did try that as well.  It didn't work either.  Thought you'd just omitted the &&'s because the command didn't make much sense as it was.

It's plain shell syntax to a program with the given environment variables set:

```
$ DISPLAY=bla XAUTHORITY=foobar sh -c 'echo $DISPLAY $XAUTHORITY'
bla foobar

```

Setting $DISPLAY and $XAUTHORITY like this should give you permission to access the X display. 

As I don't use amarok I don't know if it needs something else to run, like access to some KDE services. Use
```
DISPLAY=:0 XAUTHORITY=~/.Xauthority /usr/bin/amarok -p 2> ~/amarok.log
```
to write error messages to ~/amarok.log

---

### Post by r-mo on 2009-11-06
Sorry about that.  I use the terminal a fair amount but I'm still not a pro with it just yet.  Does that mean DISPLAY=:0 /usr/bin/amarok -p would have worked in crontab pre-karmic?

contents of amarok.log follows:

```

<unknown program name>(5201)/: KUniqueApplication: Cannot find the D-Bus session server:  "/bin/dbus-launch terminated abnormally with the following error: No protocol specified
Autolaunch error: X11 initialization failed.
" 

<unknown program name>(5200)/: KUniqueApplication: Pipe closed unexpectedly.

```

Thanks for all your help.

---

### Post by r-mo on 2009-11-15
Just tried this method to run gedit and that doesn't work either.  The output of the logfile is

```

No protocol specified

(gedit:3635): Gtk-WARNING **: cannot open display: :0

```

---

### Post by crysys on 2009-11-25
This doesn't work for me either.  Luckily 'xhost +local:' does work here so I'll be going back to that.

---

### Post by r-mo on 2009-12-09
On my work computer I was testing this on I still have the entry in crontab to launch Amarok.  After yesterdays update Amarok popped up.  Going to check it on my machine at home as well but it looks like this may have been a bug rather than me doing something wrong :D

---

### Post by r-mo on 2009-12-11
Yep, it works perfectly after the recent updates to the kernel and XOrg.

---

