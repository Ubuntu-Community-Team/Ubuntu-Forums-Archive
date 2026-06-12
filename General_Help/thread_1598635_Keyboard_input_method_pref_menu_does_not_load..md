---
title: "Keyboard input method pref menu does not load."
date: 2010-10-16
forum: General Help
---

### Post by hirakata on 2010-10-16
I'm running Maverick, trying to change my input method from IBus to Anthy (Japanese) but whenever I click on System > Preferences > Keyboard Input Methods, it won't load the preferences window. It'll say "Starting..." on the taskbar but then disappear. The usual keyboard shortcut does nothing.
What can I do to change the input method?

---

### Post by kumaryu on 2010-10-17
1. If you've upgraded from previous versions of Ubuntu, or installed other input frameworks in the past, use Synaptic (System>>Administration>>Synaptic Package Manager) to uninstall any and all of t he following: SCIM, IBUS, UIM and/or Anthy. (select item, "mark for removal", "Apply")

2. Once they've all been removed, reinstall IBUS.
3. Goto System>>Administration>>Language Support. Ensure that the keyboard input method selected is IBUS.
4. Click on Remove/Install Languages. Select Japanese. Make sure you also place a tick mark in the boxes for "input Method" and "Extra Fonts" (this will install Anthy for Ibus).
5. After completing this step, go to "Keyboard Input Methods" preferences and add Anthy to the list of input methods.

---

### Post by hirakata on 2010-10-17
That's exactly what I did. My problem is that once I get to step 5, I'm stuck because the preferences window will not open. I click on it in the menu, and a taskbar item appears, but then it disappears after a few moments. I don't get a window or anything. Is there a way to bypass the GUI altogether and do it through the terminal, since clearly it won't work to just click on things?

---

### Post by kumaryu on 2010-10-19
From the terminal, you could try:
im-switch -c
to bring up a menu to switch input method. This assumes however that Ibus daemon is running.

ibus-daemon -d
will start the daemon if its stopped for some reason.


Your problem sounds a bit similar to the symptoms described in this thread:
[http://ubuntuforums.org/showthread.php?t=1595826](http://ubuntuforums.org/showthread.php?t=1595826)

---

### Post by Ni-el on 2010-10-29
I just spent an hour today with a similar problem after upgrade to Maverick.
After reinstalling everything the same problem exists...
Try using keyboard shortcut Ctrl + Space to switch to Anthy instead of clicking on the menu. There may be some linking error in the graphical menues.

---

