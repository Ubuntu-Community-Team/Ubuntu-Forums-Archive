---
title: "Screensaver w/ real Desktop"
date: 2011-01-10
forum: General Help
---

### Post by scu-ba-de-buntu on 2011-01-10
I need a locked 'screensaver' that shows the real background/desktop (icons and open windows) so that my boss can **see** what I was working on, but my peers can't mess with it. All the Ubuntu screensavers as far as I can tell either manipulate pictures or do some 3D/2D graphics.


Thanks!

---

### Post by JCM_Pico on 2011-01-10
Try setting a screenshot of your desktop in pictures folder and set it as the screensaver... 
It may work and its simple

---

### Post by stinkeye on 2011-01-10
```
sudo apt-get install xtrlock
```
Read man xtrlock before use.

You can run manually by creating a panel launcher or keyboard shortcut.

or 

use in combination with **xautolock** to take the place of your screensaver.
In screensaver preferences turn off activate screensaver and lockscreen.

Download xautolock
```
sudo apt-get install xautolock
```

Save this script as **myscreenlock**
```
#!/bin/bash

xautolock [COLOR="Magenta"]-notify 10[/COLOR] -notifier 'notify-send "Screen will lock in 10 seconds"' [COLOR="DarkOrchid"]-time 5[/COLOR] -locker "xtrlock"
```
Right click Properties > Permissions and tick execute.
[COLOR="Magenta"]-notify 10[/COLOR]...sends notification 10 secs before screen locks
[COLOR="#9932cc"]-time 5[/COLOR]...idle time(minutes) before screen locks.


Add to startup applications by using the browse button to link to where
you saved **myscreenlock**.

You may have to install the libnotify1 package for the notify-send command to work.
```
sudo apt-get install libnotify1
```

---

### Post by Snze on 2011-01-10
Hiya - for some reason I can't get this to work.

Running xautolock in a terminal gives nothing to work with :confused:

I'm running Maverick, and I'm stumped.

Any thoughts?

---

### Post by scu-ba-de-buntu on 2011-01-10
Thanks stinkeye: xtrlock works great!


> **Snze said:**
> Hiya - for some reason I can't get this to work.

Running xautolock in a terminal gives nothing to work with :confused:

I'm running Maverick, and I'm stumped.

Any thoughts?

What do you mean? I have not yet tried xautolock, but xtrlock just lets you type it in, as its the active application.

---

### Post by stinkeye on 2011-01-10
If you want to run xautolock without using any options you need to install
**xlockmore-gl** which it uses as the default locker.

Then if you run the command **xautolock**, after the default 10 mins idle time xlockmore-gl will kick in, lock the screen and display a screensaver.

In the terminal enter 
```
man xautolock
``` for info on options.

xtrlock is another program which instantly locks the screen (screen remains visible and the mouse cursor transforms into a padlock) and can be specified as the **-locker** to use with xautolock, as shown in previous post.

Running xautolock with no options isn't very useful as you may as well just use the screensaver.

It's only really useful when using the options to specify what happens when the computer is idle after a set amount of time.
eg instead of showing a screensaver, lock the screen with xtrlock.

---

### Post by Snze on 2011-01-10
Thanks for the responses... and sorry for a vague previous post.  I was partially thread jacking because it sounded like stinkeye has some experience with xautolock, which has been winding me up lately.

Anyway, i've solved my issue too.  Xautolock is a great app when it works, as you can get it to do anything you want after a period of idleness, such as running a script to close certain programs or mute audio - whatever you need. However,it looks like it doesn't play nice with gnome-power-manager; when I killed the daemon, xautolock started working :D

---

### Post by williamts99 on 2011-02-14
I found xtrlock from this post, thank you very much.  If you want to use it with a keyboard shortcut, see my post #4 [http://ubuntuforums.org/showthread.php?p=10457105](http://ubuntuforums.org/showthread.php?p=10457105)

---

