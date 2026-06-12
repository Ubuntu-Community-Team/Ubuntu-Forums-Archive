---
title: "How do you lock your desktop without activating the screen-saver ?"
date: 2010-07-17
forum: General Help
---

### Post by ProgramErgoSum on 2010-07-17
Currently, when I lock the desktop, the screen-saver is immediately activated. Is it not possible to activate the screen-saver a few minutes after the screen is locked ? And, while the desktop is locked, can the wall-paper still be seen until the screen-saver comes in ?

I have a cute wall-paper which I want to display. ;) 

Also, I am strict about maintaining a 'clean' desktop and you will very rarely find any icons on my desktop. (Because, all files are filed under 'Misc' folder. ;) Kidding...I really do maintain strict folder level, always save files at the right folder and ruthlessly delete 'un-wanted' files.) So, it's ok for the desktop/wall-paper to be seen when the desktop is locked and screen-saver is yet to come in.

---

### Post by AlphaLexman on 2010-07-17
Ctrl + Alt + l (lowercase L) should normally do the trick.

If not, check System, Preferences, Keyboard Shortcuts, Desktop, Lock Screen. 

From there you can set any unused keyboard sequence to lock the screen without a screensaver.

---

### Post by ProgramErgoSum on 2010-07-18
uh...no, that did not work.

It locks and activates the screen-saver. I looked at the Screen-saver settings too. I don't see an option to 'start screen saver when desktop is locked' that I could un-check.

---

### Post by Vaphell on 2010-07-18
i read a little and it looks like the screensaver is responsible for screenlock and it's invoked with lock now option. As a proof - you can disable screensaver altogether in preferences and still you'll get it at CTRL+ALT+L.
Apparently there is no standalone 'lock screen' option in the system though it doesn't make much sense. What if i want to lock screen and have login prompt clearly visible at all times?

---

### Post by stinkeye on 2010-07-18
You can lock the screen and still see the desktop with xtrlock.
It's in the software centre.

From man xtrlock:
```
DESCRIPTION
       xtrlock locks the X server till the user enters their password  at  the
       keyboard.

       While  xtrlock  is  running, the mouse and keyboard are grabbed and the
       mouse cursor becomes a padlock.  Output displayed by  X  programs,  and
       windows  put  up  by new X clients, continue to be visible, and any new
       output is displayed normally.

       The mouse and keyboard are returned when the user types their password,
       followed  by Enter or Newline.  If an incorrect password is entered the
       bell is sounded.  Pressing Backspace or Delete erases one character  of
       a  password  partially  typed; pressing Escape or Clear clears anything
       that has been entered.

       If too many attempts are made in too short a  time  further  keystrokes
       generate bells and are otherwise ignored until a timeout has expired.

```

I don't think the screensaver kicks in though.

---

### Post by ProgramErgoSum on 2010-07-21
Well, that is complicated for a simple request.

I think, this should be a screen saver option such as, 'Do not activate screen saver when locked until *n* minutes after locking'. But, I don't see such an option.

---

### Post by Leeteq on 2010-08-30
Second that, should be possible to lock the screen and only show the desktop, with two options; either the desktop with its "elements", or (default) just the currently active desktop background image without any other information. A security concern if windows etc. should pop up and display during a locked state...

---

### Post by sgosnell on 2010-08-30
Why not just use the image you have on your desktop as the screensaver?

---

### Post by williamts99 on 2011-02-14
> **ProgramErgoSum said:**
> Well, that is complicated for a simple request.

I think, this should be a screen saver option such as, 'Do not activate screen saver when locked until *n* minutes after locking'. But, I don't see such an option.

You can create a script that will sleep and then activate the screen-saver, or xtrlock.

See my post #4 at [http://ubuntuforums.org/showthread.php?p=10457105](http://ubuntuforums.org/showthread.php?p=10457105) all you would have to change is how long you want it to sleep before activation.

---

