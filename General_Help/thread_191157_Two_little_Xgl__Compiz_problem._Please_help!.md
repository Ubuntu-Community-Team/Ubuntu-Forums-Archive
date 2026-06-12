---
title: "Two little Xgl / Compiz problem. Please help!"
date: 2006-06-07
forum: General Help
---

### Post by nemesa on 2006-06-07
Hi!

I've got only two minor xgl/compiz problem right now.

**1,**

I can't use my ALT / ALT Gr keys.
If I do this...
```
xmodmap /usr/share/xmodmap/xmodmap.hu
```
...all my compiz shortcuts are stop working.

I think something like this could help, but I can't figure it out how to modify:
```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```
(Posted by panurge77, to prevent Shift+Backspace gnome restart)


**2,**

After I login into the Xgl gnome session, the splash stays on the screen. I can use anything, but it stays on the desktop. After about 1 min. it disappears... and the programs in the "System / Preferences / Sessions / 3rd tab" start (sorry I have hungarian ubuntu).

I'm using the following session:

```

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```

And my /usr/bin/startxgl.sh:

```

#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize
place menu switcher &
# Start GNOME
exec gnome-session

```

taken from [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916) (great guide)

XGL / Compiz is damn cool and usable. Please help me to fix these problems...

---

### Post by Flyn on 2006-06-07
I dunno about the second problem, but you might want to try rebinding the shorcuts after using xmodmap, cause the keys can change names (for example, from "Super_L" to "Meta_L")
Hope this helps.

---

### Post by nemesa on 2006-06-07
I don't know what are the new names... I've tried in compiztools to replace <Alt> with <Alt_L> or <Shift> with <Shift_R> but nothing happend

(when I restarted compiztools the <Shift_R>, <Control_L>, <Alt_L> like bindings disappeared) I don't find these shortcut entries in the gconf-editor...

---

### Post by Flyn on 2006-06-07
Try binding short cuts in the System->Preferences->Keyboard Shortcuts and see what it enters them as.

---

### Post by panurge77 on 2006-06-07
I dont remember what causes this splash screen to stay, but you can search compiz forums for an explanation, I've read it there once:
[http://compiz.net](http://compiz.net)
Anyway, the easier way to avoid it is disabling the splash screen on the sessions configuration. Also the should go away if you click it but if your session startup is taking so long the problem might be xgl is taking a long time to initialize. I never used xgl as a session, and I'm on nvidia, so I dont know about ati tricks, but maybe you can compare your configuration with similar howtos and look for something different.

---

### Post by nemesa on 2006-06-07
> 
Try binding short cuts in the System->Preferences->Keyboard Shortcuts and see what it enters them as.


It works great now! THANK YOU! I needed to add a plus <Mod2> after every <Alt><Control><Shift> bindings. Just another question: which key is the <Super>?

I'm searching for the solution of the first problem...

---

### Post by Jeff Johnston on 2006-06-07
For your first problem this might help, although not really a solution. I also have to go select a different keyboard, and then set it back for my shortcuts to work. Luckily I never reboot my computer :).

[http://ubuntuforums.org/showthread.php?t=185350&highlight=XGL+keyboard+shortcuts](http://ubuntuforums.org/showthread.php?t=185350&highlight=XGL+keyboard+shortcuts)

---

### Post by Flyn on 2006-06-07
[quote=nemesa]It works great now! THANK YOU! I needed to add a plus <Mod2> after every <Alt><Control><Shift> bindings. Just another question: which key is the <Super>?

I'm searching for the solution of the first problem...[/quote] 
Well, maybe you can try using what I use for your startxgl and startcompiz:

startcompiz:
```
killall gnome-window-decorator
wait
gnome-window-decorator & DISPLAY=:1
LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz --replace gconf
#fixes the shift-backspace bug
xmodmap /usr/share/xmodmap/xmodmap.us-101
``` 
startxgl:
```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# Start GNOME
exec gnome-session

```

---

### Post by nemesa on 2006-06-07
Thank you guys!!

Now both of the problems gone with this howto (and a little edit):

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

If anybody run into this problem:

/usr/bin/startxgl.sh:

```

#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec gnome-session

```

/usr/bin/startcompiz
```

#!/bin/sh
killall gnome-window-decorator
wait

gnome-window-decorator &
compiz --replace gconf &
xmodmap /usr/share/xmodmap/xmodmap.hu

```

run startcompiz from System / Sessions / 3rd tab

This is a briliant comunity,
thank you so much you helped me.

:D :D :D

---

