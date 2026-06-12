---
title: "Tablet problems in GIMP"
date: 2010-05-31
forum: General Help
---

### Post by bobthechemist on 2010-05-31
Hi all,

  I'm running lucid 64bit.  Installed driver for my Genius 8x6 per the howtos in the forum without difficulty.  Calibration and pressure sensitivity work in Gimp (2.6) however if pressure sensitivity is set to screen, I get unusual behavior in the save window.  None of the sliders, buttons, or textboxes accept input.  The only way out is to hit the "X" in the window bar.  If I disable the pressure sensitivity, the save box regains its expected functionality.  Some things I've tried:

1. Happens independent of window manager (tried compiz and metacity)
2. Other save dialogs work fine (when Gimp not working, opened a Gedit window, which worked as expected).
3. Keyboard shortcuts and navigation in the save dialog work properly.

I don't have another pressure sensitive app installed, so I can't tell if this problem is specific to Gimp yet.

Any ideas?

---

### Post by cywhale on 2010-07-03
Similar problem here, I was not able to use touchpad-/mouseclicks e.g. in "Save as"- and "Scale layer"-windows.
The solution for me was to set the mode of all devices to "disabled" in the extended input devices options, only device working in "screen"-mode is the Wacom Graphire4 stylus. Now everything seems to work fine here (including pressure sensitivity using the Graphire4 stylus).

---

