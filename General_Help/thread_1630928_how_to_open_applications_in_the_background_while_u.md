---
title: "how to open applications in the background while using terminal?"
date: 2010-11-25
forum: General Help
---

### Post by princeofnam on 2010-11-25
it's really easy to launch an application using alt+f2 without having to worry about it while it's running but in terminal the window must remain open and you can't run anything else while the application is running e.g. firefox, rhythmbox.  does anyone know how to run applications in the background while using terminal?

---

### Post by bodhi.zazen on 2010-11-25
> **princeofnam said:**
> it's really easy to launch an application using alt+f2 without having to worry about it while it's running but in terminal the window must remain open and you can't run anything else while the application is running e.g. firefox, rhythmbox.  does anyone know how to run applications in the background while using terminal?

To put the application into the background, use &

```
command &
```

If you wish to close the terminal, and keep the application running, you can use several options. 

screen, dtach, and nohup.

```
nohup command &
```

screen is helpful as you can re-start a session and dtach is fun as well

[http://www.cyberciti.biz/tips/how-to-use-screen-command-under-linux.html](http://www.cyberciti.biz/tips/how-to-use-screen-command-under-linux.html)

[http://linux.die.net/man/1/dtach](http://linux.die.net/man/1/dtach)

---

### Post by princeofnam on 2010-11-26
yeah "command &" and then typing "screen" works perfectly.  though i'm still confused about what's going on.  Does the "&" automatically launch the screen application?  I tried reading the Screen link you sent me, but i still don't understand what exactly it's for.  to open multiple terminals in one window?

nohup didn't exactly work for me

> sushi@Tyrork:~$ nohup firefox &
[1] 21718
sushi@Tyrork:~$ nohup: ignoring input and appending output to `nohup.out'


---

### Post by matt_symes on 2010-11-26
Hi

> **princeofnam said:**
> yeah "command &" and then typing "screen" works perfectly.  though i'm still confused about what's going on.  Does the "&" automatically launch the screen application?  I tried reading the Screen link you sent me, but i still don't understand what exactly it's for.  to open multiple terminals in one window?

Yes. Screen is a program that allows you to have multiple terminal sessions open. Read up on screen attach, detach. (One of the best utilities written for *nix, great for ssh) Crtl +a and c to create a new screen.

Command + & Runs the command as as a background process.

nohup runs a command that will not stop when the terminal is closed (No hangup).

Kind regards

---

### Post by princeofnam on 2010-11-26
awesome.  if command + & runs the application, etc. as a background status why does it not do it automatically?  I always have to type screen afterwards.

speaking of screen i always get the disclaimer before starting.  is there a way to get rid of that?

---

### Post by princeofnam on 2010-11-26
okay this time i didn't have to type screen afterwards.

maybe the first few times were outliers

---

### Post by matt_symes on 2010-11-26
Hi

> 
awesome.  if command + & runs the application, etc. as a background  status why does it not do it automatically?  I always have to type  screen afterwards. I'm glad you like screen :) You don't have to run screen as a background process because ctrl A + C forks a new child shell for you.

at a terminal type

ps aux | grep bash

type screen and ctrl +a then c a number of times to fork some shells then type

ps aux | grep bash

again....... and count the number of shells (assumes your using bash)

Kind regards

---

### Post by nothingspecial on 2010-11-26
Try typing ```
byobu
``` instead of screen.

It`s ubuntu`s pimped up version of screen.

You get a status bar, with indicators, such as battery life, network traffic etc - like a panel.

If you close the terminal, everything carries on.

Even a remote one - useful if you are logged on to your server from your laptop and the battery runs out etc.

Get a new "window" with F2 and navigate with F3 and F4

There`s loads of other useful stuff you can do, with byobu/screen......

...... except ,afaik, you can`t use the framebuffer.........

But then we have more than one tty :D

---

### Post by matt_symes on 2010-11-26
Hi

> **nothingspecial said:**
> Try typing ```
byobu
``` instead of screen.

It`s ubuntu`s pimped up version of screen.

You get a status bar, with indicators, such as battery life, network traffic etc - like a panel.

If you close the terminal, everything carries on.

Even a remote one - useful if you are logged on to your server from your laptop and the battery runs out etc.

Get a new "window" with F2 and navigate with F3 and F4

There`s loads of other useful stuff you can do, with byobu/screen......

...... except ,afaik, you can`t use the framebuffer.........

But then we have more than one tty :D

Nice. Good call. :popcorn:

Kind regards

---

### Post by nothingspecial on 2010-11-26
> **matt_symes said:**
> Hi



Nice. Good call. :popcorn:

Kind regards

Thankyou ......

...... I`m getting full ;)

---

### Post by bodhi.zazen on 2010-11-26
> **princeofnam said:**
> yeah "command &" and then typing "screen" works perfectly.  though i'm still confused about what's going on.  Does the "&" automatically launch the screen application?  I tried reading the Screen link you sent me, but i still don't understand what exactly it's for.  to open multiple terminals in one window?

nohup didn't exactly work for me

 That output is normal.

firefox should start normally and you should be able to close your terminal.

nohup.out is a log file.

You can re-direct the output:

```
nohup firefox >/dev/null 2>&1 &
```

You can write an alias for that in ~/.bashrc if you wish.

Note: Oh, it does not work for firefox because firefox is a link to firefox-bin.

Wrap it in a sub-shell

```
(firefox >/dev/null 2>&1 &)
```

No no-hup with a sub-shell.

Most applications work with nohup though.

Glad you like screen, see the link I gave you earlier.

See also:

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

dtach is similar but "light weight" =/

---

