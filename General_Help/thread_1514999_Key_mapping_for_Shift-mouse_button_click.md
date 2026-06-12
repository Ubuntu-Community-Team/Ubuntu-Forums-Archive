---
title: "Key mapping for Shift-mouse button click?"
date: 2010-06-21
forum: General Help
---

### Post by KonfuseKitty on 2010-06-21
I have successfully mapped the plus-minus key on the keyboard to emulate the Wheel/Middle Mouse Button click with this shell script run at startup:

```
#!/bin/sh
xmodmap -e "keycode 49 = Pointer_Button2"
xkbset m
```This is so I can rotate the view in Blender without clicking the wheel, because the wheel also zooms, and it's too easy to zoom inadvertently. The remaining problem is panning, a Shift-MMB combination. Now I'm lost - how can I map a key (or better still, a Shift-key combo) to the Shift-MMB click?

---

### Post by KonfuseKitty on 2010-06-24
No-one knows?

Well, I've created a bit of a clunky solution by swapping the middle and right buttons, then mapping the right button (now actuated by pressing the middle button) to the plus-minus key on the keyboard.  This way I can avoid clicking the middle button altogether.  To bring up a contextual menu, I just press the plus-minus key on the keyboard.  And in Blender I can rotate with the right button and pan with Shift-right-button. Here's the script (9 is the mouse ID):

```
#!/bin/sh
xinput set-button-map 9 1 3 2
xmodmap -e "keycode 49 = Pointer_Button3"
xkbset m
```

The problem now is that when this is run at startup, only the mouse button remapping is active, the key mapping isn't.  But if I then run the script manually, the key mapping is done.  What could be the cause of this?  Would I be right in suspecting xkbset is the culprit?  Maybe it doesn't load up until very late in the startup procedure?  I thought of this and prefixed the script name with "xx" to make it load last in the list of startup applications, but that hasn't solved it.

---

### Post by KonfuseKitty on 2010-06-26
I have found no solution to the script not executing properly at startup and have resigned myself to the fact that I'll have to run the script manually.  This gave me the idea that the script should be conditional, so I could toggle the remapping on and off as desired.  I only need the remapping in Blender, I would toggle it back to default when working in other programs.  I altered the script:

```
#!/bin/sh
if [ xinput get-button-map 9 = "1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 " ]
then
	xinput set-button-map 9 1 3 2
	xmodmap -e "keycode 49 = Pointer_Button3"
	xkbset m
else
	xinput set-button-map 9 1 2 3
fi
```

...but it doesn't work, remapping is never done.  BTW, the "1 2 3 ..." part of the conditional expression is what I obtained from terminal, including the space after 16.  I tried it without the space, but it makes no difference.  Where am I going wrong?

I would also like to know how I can test for a value containing another rather than comparing the entire values.  How can I script "if x contains y" rather than just "if x equals y"?

---

