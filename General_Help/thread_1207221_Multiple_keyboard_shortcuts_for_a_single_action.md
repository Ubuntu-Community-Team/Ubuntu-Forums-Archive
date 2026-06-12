---
title: "Multiple keyboard shortcuts for a single action"
date: 2009-07-07
forum: General Help
---

### Post by wizard04 on 2009-07-07
I'm trying to create an additional shortcut for "Close window", besides the default Alt+F4.  More specifically, I have a Logitech MX Revolution mouse and would like to have the Search button close windows.  I have been able to assign commands to the other buttons using xbindkeys, but have found that the Search button actually shows up as a keyboard button, XF86Search (c:225), and have not been successful in creating a macro for that key code.  If I change the default shortcut for "Close window" in System-->Preferences-->Keyboard Shortcuts to XF86Search, it works as expected, though Alt+F4 no longer works, of course.

If I could have both Alt+F4 and XF86Search assigned to the "Close window" action, I would be all set.  Is this possible?

Side note: occassionally, the Search button *does* show up as a mouse button (b:10) instead of a key, but I don't know what triggers it.  If I reboot the computer it goes back to being a keyboard button.

Any help is appreciated!

---

### Post by tgalati4 on 2009-07-08
man xmodmap

I think you can assign multiple key definitions in xmodmaprc.  Up to 8 keys per function, but only 4 is used by xorg.  It's the Gnome desktop that confuses the use of xmodmaprc keyboard shortcuts.  If you assign functions via xmodmaprc and not assign them in Gnome--Keyboard-Shortcuts, it may work.  Of course, there may be a method to assign multiple keys to the same function in Gnome.  I just don't know how to do it.

When you create an xmodmaprc file in your home directory and reboot, a dialog box pops up asking whether you want X-server key bindings or Gnome key bindings.

When you use X-server key bindings, expect some Gnome breakage.  It's non-trivial to get all the extra keys in all applications working properly.

---

### Post by wizard04 on 2009-07-08
Would you have an example of how to assign a function with xmodmap?

As far as I understand, xmodmap just maps keysyms to keycodes (and variations with shift & mode_switch modifiers).  I see no way to assign a function (e.g., Close window) to a keycode, nor to assign a keysym combination (e.g., Alt+F4).

---

### Post by tgalati4 on 2009-07-08
Search the forums.  I've posted a few examples.  

setkeys assigns keycodes.  Xmodmap maps keys to X-Windows functions--many of which work in the gnome desktop.

---

### Post by dnquark on 2009-07-21
I am currently looking for the solution to the exact same problem.  Essentially, what needs to happen is a remapping of keycode 225 to a keyboard shortcut, e.g. Ctrl-w.  

One way to do it is to use xmacroplay together with xbindkeys using this line in .xbindkeysrc:
"echo -e 'KeyStrPress Control_L\nKeyStrPress w\nKeyStrRelease w\nKeyStrRelease Control_L' | xmacroplay :0 &" 
  c:225

However, I cannot figure out how to modify my xmodmap -- I did
modmap -pke > .xmodmaprc
edited the file and put
xmodmap ~/.xmodmaprc 
into ~/.xsession -- but this gives an error and doesn't allow me to log in.  What am I doing wrong?..

---

