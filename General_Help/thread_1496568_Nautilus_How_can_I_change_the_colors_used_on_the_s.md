---
title: "Nautilus: How can I change the colors used on the scroll bar?"
date: 2010-05-29
forum: General Help
---

### Post by RobertL on 2010-05-29
In 10.04 Lucid my Nautilus scroll bars are white. The scroll bar slider (the icon that can be moved up and down with the cursor to scroll the window) is the exact same shade of white and the slider outline is pale grey. The lack of color contrast makes the slider hard to see. Is there a preference item somewhere that lets me change this color scheme? I expected to find it in System >> Preferences >> Appearance >> Theme but I don't think there's anything there about the scroll bars. Am I missing it?

I think my monitor might be more contrasty than most, which is probably exacerbating the problem, but this is what I have to work with. I would rather fix it by changing a system setting than replacing the monitor.

---

### Post by jerenept on 2010-05-29
You might want to try another theme, like clearlooks or something.

---

### Post by RobertL on 2010-05-29
> **jerenept said:**
> You might want to try another theme, like clearlooks or something.

You're right. I had tried a few different theme choices and they didn't change the white-on-white slider color but clearlooks does. I can't imagine why any theme uses white-on-white.

---

### Post by dino99 on 2010-05-29
have a closer look at themes: each one can be tweaked with their tabs settings

---

### Post by stinkeye on 2010-05-29
Install **gnome-color-chooser** and you can change your scroll bar color 
in the tab titled "specific".

---

### Post by naptastic on 2011-10-17
Add these lines to ~/.gtkrc-2.0:

  style "gnome-color-chooser-scrollbar"
  {
    bg[NORMAL] = "#F07746"
    bg[PRELIGHT] = "#D76A3E"
    bg[ACTIVE] = "#BD5D37"
  }
  widget_class "*Scrollbar" style "gnome-color-chooser-scrollbar"

Change the hex color values to what you like. Prelight is the color while the mouse is hovering over the scrollbar, and active is the color while it's being held down.

---

### Post by drachenchen on 2011-12-05
I'd recommend Gnome Color Chooser ONLY if your monitor can do better than 1024x768 resolution.  At least in Lucid, there's no way to re-size the program's default window, which is too tall for 1024x768.  Result: the "Apply" and "Revert" buttons are off the screen, and no way to get at them.  Sad, since it appears that people who CAN use it, love it.  Had this problem with earlier Ubuntus, too.

-And yes, I tried Alt+F8, and Alt+(Middle-Mouse-Button), and Alt+(arrow keys).  No joy.  System>Preferences>Keyboard_Shortcuts tells me that Alt+F8 is the right shortcut to resize windows, but at least with this app, on Lucid, that would be False.  Already tried System>Preferences>Monitors also.  Neither of my monitors has a res higher than 1024x768 listed, so I can't use that approach, either.

A lame chain reaction of minor oversights on the part of all concerned.  Rather frustrating... ](*,)

---

