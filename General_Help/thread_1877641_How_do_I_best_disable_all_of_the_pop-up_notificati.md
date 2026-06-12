---
title: "How do I best disable all of the pop-up notifications?"
date: 2011-11-08
forum: General Help
---

### Post by nickleboyblue on 2011-11-08
Problem: The Ubuntu Unity notification area likes to pop up notifications from facebook, network, etc.  This is fine during normal computer use, but these notifications even pop up while using software that should be the only focus of the screen, like some games.  This slows down the graphics and causes lag problems that are extremely annoying.  While there should (and might) be a mechanism for turning off all notifications automatically when focused software is running, it doesn't work for me.  So, here's the question: How do I easily disable and re-enable all notifications so I can use my software in peace?

Reasoning: notifications shouldn't pop up always.  They should be inhibited every once in a while. Turn them off automatically when it makes sense to do so, and turn them back on again when it doesn't. for example, if anything is running full-screen on the current workspace, turn them off!

Any help here would be nice.

---

### Post by philinux on 2011-11-08
> **nickleboyblue said:**
> Problem: The Ubuntu Unity notification area likes to pop up notifications from facebook, network, etc.  This is fine during normal computer use, but these notifications even pop up while using software that should be the only focus of the screen, like some games.  This slows down the graphics and causes lag problems that are extremely annoying.  While there should (and might) be a mechanism for turning off all notifications automatically when focused software is running, it doesn't work for me.  So, here's the question: How do I easily disable and re-enable all notifications so I can use my software in peace?

Reasoning: notifications shouldn't pop up always.  They should be inhibited every once in a while. Turn them off automatically when it makes sense to do so, and turn them back on again when it doesn't. for example, if anything is running full-screen on the current workspace, turn them off!

Any help here would be nice.
[https://wiki.ubuntu.com/NotifyOSD/Comments](https://wiki.ubuntu.com/NotifyOSD/Comments)

ctrl f and search disable

The command can be reversed. I've never tried this so Caveat Emptor.

---

### Post by stinkeye on 2011-11-08
I just open up system monitor and right click on notify-osd and use
**Stop Process **
and
**Continue Process**

---

### Post by philinux on 2011-11-08
> **stinkeye said:**
> I just open up system monitor and right click on notify-osd and use
**Stop Process **
and
**Continue Process**

+1 if that's what the OP needs.

---

### Post by jerrrys on 2011-11-08
/usr/lib/notify-osd

I think if you rename this file, that will remove all notifications.

---

### Post by nickleboyblue on 2011-11-08
> **stinkeye said:**
> I just open up system monitor and right click on notify-osd and use
**Stop Process **
and
**Continue Process**

This is exactly what I need.  That should help my games and whatnot flow a bit smoother without interruption and without the graphics trying to compute both a notification and the game at the same time, slowing things down.  Thanks a ton!

A lot of the above answers work for different purposes, as I can see why someone would want to disable all notifications, but this one is easy, graphical, and reversible, which is what I need (I like notifications, but only when it makes sense with what I am doing).

---

### Post by Rebelli0us on 2011-11-08
The only useful one is the sound volume. Is there a way to disable all except that one?

---

### Post by stinkeye on 2011-11-09
Firstly because I don't fully understand bash scripting I make scripts
by looking at other scripts I've downloaded and do copy/paste jobs.

I found that when notify-osd is stopped
```
ps aux | grep notify-osd
```
gives a status of [COLOR="Red"]Tl[/COLOR]
```
glen@Oneiric:~$ ps aux | grep notify-osd
glen      1057  0.0  0.6 119608 13256 ?        [COLOR="red"]Tl[/COLOR]   12:32   0:01 /usr/lib/notify-osd/notify-osd
```

So the script outputs a count for "Tl" after grepping "notify-osd".
If the count is "0" notify-osd is stopped.
If the count does not equal "0" notify-osd is continued.

Toggle_Notifications
```
#!/bin/bash
#Script to pause notifications
# click to stop, click to continue

STATUS=$(ps aux | grep notify-osd | grep -c Tl)

if [ "$STATUS" == "0" ]
then
  exec killall -s STOP notify-osd 
else
  exec killall -s CONT notify-osd &
  notify-send -u critical "Notifications are On"

fi
exit 0
```
Bind to a shortcut key and toggle on/off.
Can someone test it to see if it works for them.
Open up system monitor and see if the status for notify-osd changes.

---

### Post by nickleboyblue on 2011-11-23
You know, it would be great to get an appindicator written in Python that would do this...  That way, you could literally turn them on or off by clicking one button.  I'll have to look into that when I get some time.  Would possibly even be a good addition to one of the existing menus, like say the settings menu or the mail menu.

---

### Post by crazy bird on 2011-11-23
will this not do the trick to get rid of that notify-osd permanently:
**[COLOR=black]sudo mv /usr/lib/notify-osd .[/COLOR]**

---

