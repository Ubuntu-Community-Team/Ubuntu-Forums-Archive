---
title: "Key mapping with GizmoD and Nostromo Speedpad n50"
date: 2010-03-25
forum: General Help
---

### Post by paraplegicpanda on 2010-03-25
I've got an old Nostromo n50 speedpad that I decided I wanted to try to get to work with WoW. I have looked into the Nostromo Linux drivers and Pystromo, but I decided to dip my toes into Python with [Gizmo Daemon]("http://sourceforge.net/apps/mediawiki/gizmod/index.php?title=How_Gizmod_Works") because I should 
be able to use it for other gamepads in the future. I'm not exactly sure what the problem is but any help would be greatly appreciated. Here's what I've done so far:

[LIST=1]
[*]Installed GizmoD from Synaptic.
[*]Read through the tutorials and HOWTOs on the [website]("http://sourceforge.net/apps/mediawiki/gizmod/index.php?title=How_Gizmod_Works").
[*]Used [FONT="Courier New"]gizmod -g[/FONT] to record the input from my Nostromo n50.
[*]Attempted to modify a GizmoD map file to do what I wanted.
[/LIST]

Up until the last part everything has been going fine. Here's the mapping of my input keys:
```

Key 01 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90001
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_A> c: 0x130 v: 0x1

Key 01 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90001
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_A> c: 0x130 v: 0x0

Key 02 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90002
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_B> c: 0x131 v: 0x1

Key 02 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90002
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_B> c: 0x131 v: 0x0

Key 03 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90003
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_C> c: 0x132 v: 0x1

Key 03 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90003
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_C> c: 0x132 v: 0x0

Key 04 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90004
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_X> c: 0x133 v: 0x1

Key 04 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90004
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_X> c: 0x133 v: 0x0

Key 05 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90005
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_Y> c: 0x134 v: 0x1

Key 05 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90005
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_Y> c: 0x134 v: 0x0

Key 06 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90006
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_Z> c: 0x135 v: 0x1

Key 06 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90006
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_Z> c: 0x135 v: 0x0

Key 07 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90007
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_TL> c: 0x136 v: 0x1

Key 07 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90007
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_TL> c: 0x136 v: 0x0

Key 08 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90008
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_TR> c: 0x137 v: 0x1

Key 08 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90008
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_TR> c: 0x137 v: 0x0

Key 09 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90009
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_TL2> c: 0x138 v: 0x1

Key 09 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x90009
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_TL2> c: 0x138 v: 0x0

Key 10 Press
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x9000a
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_TR2> c: 0x139 v: 0x1

Key 10 Release
onEvent: Standard -- /dev/input/event3 | [EV_MSC] c: 0x4 Val: 0x9000a
onEvent: Standard -- /dev/input/event3 | [EV_KEY] <BTN_TR2> c: 0x139 v: 0x0

DPAD Up
onEvent: Standard -- /dev/input/event3 | [EV_ABS] c: 0x1 Val: 0x0
onEvent: Standard -- /dev/input/event3 | [EV_ABS] c: 0x1 Val: 0x80

DPAD Down
onEvent: Standard -- /dev/input/event3 | [EV_ABS] c: 0x1 Val: 0xff
onEvent: Standard -- /dev/input/event3 | [EV_ABS] c: 0x1 Val: 0x80

DPAD Left
onEvent: Standard -- /dev/input/event3 | [EV_ABS] c: 0x0 Val: 0x0
onEvent: Standard -- /dev/input/event3 | [EV_ABS] c: 0x0 Val: 0x80

DPAD Right
onEvent: Standard -- /dev/input/event3 | [EV_ABS] c: 0x0 Val: 0xff
onEvent: Standard -- /dev/input/event3 | [EV_ABS] c: 0x0 Val: 0x80

```

The last four keys are commented out in my map file for the moment since I'm not quite sure how to do them. The map file is attached to this post. As you will see from the map file, I just want keys 01-10 to translate into my normal keyboard keys 1-9 and 0. The DPAD I want to translate into a normal WASD for gaming. I'm kind of stumped as to where to go from here. I run gizmod from a terminal, but it doesn't seem to work.


Once again, I appreciate any help!

---

### Post by paraplegicpanda on 2010-03-25
Bump... I could definitely use some help on this.

---

### Post by paraplegicpanda on 2010-04-08
Bumpity bump... I could still TOTALLY use some help with this.

---

