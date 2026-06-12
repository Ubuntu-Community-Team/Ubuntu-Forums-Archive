---
title: "Why Won't Ubuntu Read These Keys?"
date: 2011-06-13
forum: General Help
---

### Post by khoraski on 2011-06-13
I looked it up, and when I set keyboard shortcuts it should allow me to set shortcuts for the Fn key and the Windows key. But when I go to System -> Preferences -> Keyboard Shortcuts and try to set the keys to do something they won't register. It's like it can't read they exist or something. 

How can I fix this?

:popcorn:

---

### Post by khoraski on 2011-06-25
:(

---

### Post by Abir Valg on 2011-06-25
Try a console app "xev" - see if there is any reaction to those keys. if X doesn't react to those keys, neither will Gnome's Keyboard Shortcuts.

---

### Post by idoitprone on 2011-06-25
i believe that will be a little difficult. I believe fn keys are interpreted by the bios and require drive to function properly

You should be able to remapped the windows key
as abir valg said you can use xev to see which keycode the program reads

---

### Post by hawthornso23 on 2011-06-25
Some keys are treated by keyboard shortcuts as modifiers. When these are held down they modify other keys, but they don't register as key presses by themselves. You can't assign a keyboard shortcut to simply pressing a modifier key by itself. But you can assign a keyboard shortcut to a combination involving holding down one or more modifier keys while hitting a normal key. The windows key is a modifier as are control, alt and shift.

The function key is a bit different. It is also a modifier key, but its function on many laptops is hard wired and you might not therefore have much success getting keyboard shortcuts to see it.

---

### Post by tgalati4 on 2011-06-25
What is the machine make and model?  If it's an ibm thinkpad then you will have lots of goodies when loading the ibm_acpi module--it activates all of those extra function buttons.  For any other key, not controlled by the BIOS, you can use the setkeycodes function to define most other keys:

[http://ubuntuforums.org/showthread.php?t=1207221&highlight=setkeys](http://ubuntuforums.org/showthread.php?t=1207221&highlight=setkeys)

[http://ubuntuforums.org/showthread.php?t=921870&highlight=multimedia+keyboard](http://ubuntuforums.org/showthread.php?t=921870&highlight=multimedia+keyboard)

---

