---
title: "How can I alt+ctrl+delete and end processes?"
date: 2009-12-18
forum: General Help
---

### Post by bomber991 on 2009-12-18
I've figured how to pull up the System Monitor by going to System > Administration > System monitor.  It appears very similar to the task manager that pops up in windows when you press alt+ctrl+del.

Anyways, I've been downloading a few linux games, and sometimes they lock up on me.  At least for the non-full screen ones I am able to get to the system monitor.  I find the game and it's using 100% cpu, I highlight it and end process.  Just like in windows it warns me that I could lose unsaved data if I end the process.  However, unlike windows the program never closes!

Now my two questions.  First, if I'm in a fullscreen game or application and it locks up on me, how the heck do I get out of it?  ctrl+alt+d doesn't want to show the desktop when a program is running fullscreen.  Second, how can I close out these programs when they lock up?  System Monitor doesn't seem to be working for ending programs.  I remember in windows sometimes the task manager wouldn't end process on some programs too.  You would tell it to end the process but then after that it never actually ended.  I remember in those cases I used this other program called AntiFreeze that would work.  Is their something similar for Ubuntu?

Link to antifreeze: [http://www.resplendence.com/antifreeze](http://www.resplendence.com/antifreeze)

Thanks in advance for helping me.

---

### Post by x33a on 2009-12-18
There are a lot of methods to kill a process in linux.

if everything hangs, you can simply restart the xserver.
ctrl+alt+backspace restarts the xserver, but you'll have to enable it first.

to do that:

go to system -> preferences -> keyboard.
select layouts and click on layout options.
select 'key sequence to kill the X server' and enable.

also, you could press ctrl+alt+f1, this'll take you to a text console. there you could try pkill <process name>.

---

### Post by coffeeandlinux on 2009-12-18
ctrl+alt+backspace will do a restart to the login screen

You can kill an application by doing the following:

Run application dialog box (press Alt+F2)

type in xkill.

your cursor becomes a white X. Anything you left-click with this cursor will be killed. Be very careful though on what you click.

to deactivate it without killing anything, right-click anywhere.

Hope it helps.

---

### Post by thehipho on 2009-12-18
You could try pkill (process name) to end a process.

```
pkill (process name)
```

And in fullscreen try Alt-Ctrl-Backspace(if the combination isn't already disabled by default).

Goodluck.

---

### Post by staf0048 on 2009-12-18
If you have a graphical program that's giving you trouble, the easiest method I've found is to do this:

1.  Right click on your panel, then "add to panel"
2.  Search for "Force Quit" and add it to your penel.

Now every time you have an issue, simply click (left click) the icon.  It will bring up a "crosshair" type cursor and you can simply kill what ever program that's giving you trouble by clicking on said program.

It doesn't work for for fullscreen all that well though.  A work around I've found is to click on the power button on my computer, which will put my fullscreen program into a windowed mode and bring up the shutdown options.  Click cancel and *quickly* click the "force quit" icon and your program before it returns back to fullscreen.  Shotty, but it works.

---

### Post by pbrane on 2009-12-18
Most of the time you can CTRL+ALT+F2 and get a virtual terminal. Log in with your username/password, then you can kill the game. You can run 'top' and look for the program using 100% CPU and then hit 'k' to kill it. that command will ask for a PID, just enter the number under PID of the game. When asked which signal use '9'.

---

### Post by bomber991 on 2009-12-18
Thanks for the help guys, but why didn't you tell me I needed to press ctrl+alt+f7 to get back into my graphical desktop display?  I had to hit the reset button on the tower cause I couldn't figure out how to get back to the desktop.  I tried startx and that didn't seem to work.  I guess cause I was in a virtual terminal?  I don't know, I still got a lot to learn with how this os works.

I got the ctrl+alt+backspace enabled now so I'll probably just do that if everything goes fubar.  I guess that linux reliability means I don't have to restart the whole operating system but just log out and back in instead?

I will probably do the ctrl+alt+(f1-f6) and do top, then kill for when a fullscreen app locks up and do force quit for frozen windowed applications.  I tested it out and didn't enter anything for signal and it seemed to work, but I will try entering 9 next time.

---

### Post by kjohri on 2009-12-19
First, start a terminal.

Give the command,

```
ps -u <user-id>
```

where <user-id> is for the user whose process you want to kill.

From the output of *ps -u <user-id>*,

find out the process-id, (pid) of the process you wish to kill.

Finally, give the command,

```
sudo kill -9 <process-id>
```

---

### Post by x33a on 2009-12-19
> **bomber991 said:**
> Thanks for the help guys, but why didn't you tell me I needed to press ctrl+alt+f7 to get back into my graphical desktop display?
 
sorry, with experience we tend to forget some things, which might be important for starters :D

there is also, alt+sysrq+k. This is a sure shot way of killing xserver, even if ctrl+alt+backspace fails.

but, i think you'll have to enable it too.

---

### Post by 3rdalbum on 2009-12-19
> **x33a said:**
> sorry, with experience we tend to forget some things, which might be important for starters :D

there is also, alt+sysrq+k. This is a sure shot way of killing xserver, even if ctrl+alt+backspace fails.

but, i think you'll have to enable it too.

Alt-Sysrq-K is enabled by default. That's why you don't need to enable Control-Alt-Delete, but it seems that only about three or four people on the entire Ubuntu Forums knows about Alt-Sysrq-K.

---

### Post by bomber991 on 2009-12-23
Hmm I guess alt+sysreq+k is stronger than crtl+alt+backspace?  I did have gnome completely lock up on me a few days ago and wish I would have known that so I could have tried it.  I clicked on the applications menu, and as it was fading in everything just froze up completely.  Couldn't even move the mouse cursor.  Ctrl+alt+f1 didn't work and neither did ctrl+alt+bkspace.

---

### Post by americanfridge on 2009-12-23
Thanks for the information guys! :) will try it now.

---

