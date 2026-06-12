---
title: "Lost Window Control"
date: 2012-06-13
forum: General Help
---

### Post by tango_ninja on 2012-06-13
I recently upgraded to 12.04 and seem to have lost my window control.  By this I mean that every window I open no longer has a title bar.  Without the title bar, I also have no maximize, minimize, close buttons.  I also have no Window Selector in my bottom panel although I have added it many times.

I'm getting this error every now and then "Your window manager does not support *whatever*, or you are not running a window manager."

I'm logging in as Gnome, not Unity.
(see attached screenshot)

This seems to be a problem with the window manager.  Can anyone point me in the right direction?

---

### Post by mikewhatever on 2012-06-13
Looks like your graphics card doesn't support whatever window manager is running (compiz or mutter). Try Ubuntu(no effects) from the login screen.

PS: ctrl+alt+del should bring up the logout option.

---

### Post by tango_ninja on 2012-06-13
Ah, forgot to mention that I am already running Gnome (no effects).

---

### Post by mikewhatever on 2012-06-13
Try bringing up a terminal window with ctrl-alt-t. If it pops up, run the following to verify which window manager is running:

```
ps -ef | grep -e metacity -e compiz
```

If it is compiz, run 'metacity --replace'.

PS: Metacity is the window manager of Gnome Classic.

---

### Post by tango_ninja on 2012-06-13
> **mikewhatever said:**
> Try bringing up a terminal window with ctrl-alt-t. If it pops up, run the following to verify which window manager is running:

```
ps -ef | grep -e metacity -e compiz
```

If it is compiz, run 'metacity --replace'.

PS: Metacity is the window manager of Gnome Classic.

Yes, that did the trick, thank you.  Here's my output:

```
andrew@vostro:~$ ps -ef | grep -e metacity -e compiz
andrew    2979  2561  0 16:54 pts/0    00:00:00 grep --color=auto -e metacity -e compiz
andrew@vostro:~$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_fullscreen"
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_screenshot"

```

I'm not sure what went wrong there... but I now have my window functionality back.  Cheers

---

### Post by mikewhatever on 2012-06-13
ODD! The output shows that you were running neither compiz not metacity.

---

### Post by tango_ninja on 2012-06-13
> **mikewhatever said:**
> ODD! The output shows that you were running neither compiz not metacity.

It is odd... and actually that hasn't really solved my problem.  It has given me back full functionality, but only for the session.  Once I log out and log in again, I am back to square one.  Of course, running *metacity --replace* solves the problem again but only temporarily.  

I'm also getting this output:
```
andrew@vostro:~$ update-alternatives --get-selections | grep x-window-manager
x-window-manager               auto     /usr/bin/metacity
andrew@vostro:~$ update-alternatives --get-selections | grep x-session-manager
x-session-manager              auto     /usr/bin/gnome-session
```


Shall I configure the command to run on startup or is there something else I must do?

---

### Post by mikewhatever on 2012-06-13
Yea, whatever window manager is used, it either doesn't start or crashes at login. 
How about the output of **echo $DESKTOP_SESSION**?

---

### Post by tango_ninja on 2012-06-13
> **mikewhatever said:**
> Yea, whatever window manager is used, it either doesn't start or crashes at login. 
How about the output of **echo $DESKTOP_SESSION**?

```
andrew@vostro:~$ echo $DESKTOP_SESSION
gnome-fallback

```

---

### Post by mikewhatever on 2012-06-14
Not sure why it doesn't work. Looks like something is wrong with the session or with metacity.

---

