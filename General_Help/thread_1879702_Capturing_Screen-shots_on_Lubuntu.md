---
title: "Capturing Screen-shots on Lubuntu"
date: 2011-11-12
forum: General Help
---

### Post by SteveDee on 2011-11-12
Lubuntu comes with a screen capture app called "scrot" which is associated with the <Print Scrn> key.
It operates silently and saves images to a users home directory, so many users are unaware of this feature.

One way of making this more obvious to users is to send all screen-shots to the Desktop (where they can be edited, used and then removed).

**Send Print Scrn Images to Desktop:-**
In file manager, set "Show Hidden" and then navigate to your /home/{user}/.config/openbox/ directory and open lubuntu-rc.xml in a text editor.
Use the search feature to find "scrot"

There will probably be 2 instances as shown in this extract;
```

<!-- Keybinding for PrintScreen Key -->
<keybind key="Print"><action name="Execute">
<execute>scrot</execute></action></keybind>
<keybind key="A-Print"><action name="Execute">
<execute>scrot -s</execute></action></keybind>

```

You need to add a file name template and redirection to each command, e.g: '%Y-%m-%d_%S.png' -e 'mv $f ~/Desktop/'
...so your scrot commands will look like this;
```

<!-- Keybinding for PrintScreen Key -->
<keybind key="Print"><action name="Execute">
<execute>scrot '%Y-%m-%d_%S.png' -e 'mv $f ~/Desktop/'
</execute></action></keybind>
<keybind key="A-Print"><action name="Execute">
<execute>scrot -s '%Y-%m-%d_%S.png' -e 'mv $f ~/Desktop/'
</execute></action></keybind>

```
Now save your changes and re-boot your computer.

When you hit the <Print Scrn> key you should see a time-stamped image file appear on your desktop.

...so whats the 2nd scrot command for?
This is even more useful than the 1st command. If you press <alt><Print Scrn> you can then use your mouse to drag a rectangle and define just the area you want to capture.

For more information on the scrot command open a terminal and type:-
```

man scrot

```

---

### Post by Rodney9 on 2011-11-12
If you want to save the desktop in a *.jpg in say 5 sec use this - ```
scrot -d 5 desktop.jpeg
```

More here - [http://www.freesoftwaremagazine.com/columns/how_to_take_screenshots_with_scrot](http://www.freesoftwaremagazine.com/columns/how_to_take_screenshots_with_scrot)

Rodney

---

### Post by MG&amp;TL on 2011-11-12
All due respect to the devlopers, but with a normal keyboard/mouse setup, how are you going to hold Alt-far left PrntScn-far right, and move the mouse-even further right?

---

### Post by SteveDee on 2011-11-12
> **MG&TL said:**
> All due respect to the devlopers, but with a normal keyboard/mouse setup, how are you going to hold Alt-far left PrntScn-far right, and move the mouse-even further right?

Sorry its 2 operations, so do:-
 <alt><Print Scrn> then release.
 Now hold down left mouse button and drag.

When you release the mouse button, capture is complete.

Unfortunately the mouse pointer does not turn into a cross (+) which would make things a little clearer.

---

### Post by MG&amp;TL on 2011-11-12
Ahh....gotcha. :)

---

