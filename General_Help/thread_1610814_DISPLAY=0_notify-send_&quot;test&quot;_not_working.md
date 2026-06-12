---
title: "DISPLAY=:0 notify-send &quot;test&quot; not working"
date: 2010-11-01
forum: General Help
---

### Post by dionblundell on 2010-11-01
I have a script running from a hotkey,
it tries to do this:
```
DISPLAY=:0.0; notify-send "hi there"
```this worked okay in Lucid (Ubuntu 10.04), but doesn't work in Maverick 10.10
anyone with any suggestions why? Or what I should change?
I have also tried:```
DISPLAY=:0 notify-send "hi there"
``` to no avail.

---

### Post by stinkeye on 2010-11-01
I had this problem a couple of days ago where a script I have using
**DISPLAY=:0.0** failed to work.
Also just running **notify-send "hi there"** without  **DISPLAY=:0.0;** would also fail.

I found that if I clicked in the area where the notification bubble should be
it would appear.
Even though I'm using compiz as the window manager, turning off Metacity 
compositing fixed it.
gconf-editor /apps/metacity/general/compositing_manager

---

### Post by MooPi on 2010-11-01
libnotify-bin not installed by default as it's not in my list of installed packages

---

### Post by jesuisbenjamin on 2010-11-01
> **dionblundell said:**
> I have a script running from a hotkey,
it tries to do this:
```
DISPLAY=:0.0; notify-send "hi there"
```this worked okay in Lucid (Ubuntu 10.04), but doesn't work in Maverick 10.10
anyone with any suggestions why? Or what I should change?
I have also tried:```
DISPLAY=:0 notify-send "hi there"
``` to no avail.

Hi there,

I have no solution but i am interested in this thread. Is what you wrote above the entire content of your script? Is the purpose to trigger a pop-up message of the notifier?

B.

---

### Post by stinkeye on 2010-11-01
> **jesuisbenjamin said:**
> Hi there,

I have no solution but i am interested in this thread. Is what you wrote above the entire content of your script? Is the purpose to trigger a pop-up message of the notifier?

B.
Yes.
You'll need to install **libnotify-bin** as MooPi said, to use the
notify-send command.

eg this will display time and date.
```
notify-send -i clock "$(date +"%a %d %b, %l:%M %p")"
```

notify-send -i [COLOR="Magenta"]path/to/your/icon[/COLOR] "[COLOR="#ff00ff"]insert title[/COLOR]" "[COLOR="#ff00ff"]insert body[/COLOR]"

---

### Post by jesuisbenjamin on 2010-11-01
This is great! :popcorn:

But few questions: if i need to install libnotify-bin to manage to do that, how is Ubuntu already able to send notification messages? What is the relationship between this package and the notify-osd deamon running on Ubuntu? Finally what is the relationship between libnotify-bin and the command notify-send (normally the command and the package name are identical aren't they?)

Thanks!
B.

---

### Post by dionblundell on 2010-11-01
metacity is already turned off for me, and notify-send still does not work.

I installed libnotify

libnotify (notify-send) makes use of dbus to get a pop-up, it is essentially a user interface.

I have tried turning of compiz, to no avail too.

Anyone else, with another idea?

---

### Post by dionblundell on 2010-11-06
Discovered that the problem is with "X server security." The issue is that root is trying to lunch something on someone elses display, and this is not allowed. The way around this is: ```
xhost +local:
``` I just added this line to my script and everything works okay now.

---

### Post by jesuisbenjamin on 2010-11-06
> **dionblundell said:**
> 
libnotify (notify-send) makes use of dbus to get a pop-up, it is essentially a user interface.

Hi there,

I tried to look for information on the Dbus and Libnotify but have found either too superficial or too complex info. Do you have any information on this? I'd like to play around with notifications and learn at the same time.

Thanks.
B.

---

### Post by rickyrockrat on 2010-11-16
I just posted this, which should take you step-by-step.

[http://ubuntuforums.org/showthread.php?t=1623135](http://ubuntuforums.org/showthread.php?t=1623135)

---

