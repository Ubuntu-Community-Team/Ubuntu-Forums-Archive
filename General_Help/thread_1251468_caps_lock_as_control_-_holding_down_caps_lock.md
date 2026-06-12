---
title: "caps lock as control - holding down caps lock"
date: 2009-08-27
forum: General Help
---

### Post by blackandwhitepandabear on 2009-08-27
Hi!

I am trying to let caps lock be an additional control key in Hardy Heron. I know there are many pages on this topic, which suggests one of two things:
1) make changes through the System -> Preferences -> Keyboard, [Layout Options].
2) edit .Xmodmap and remap ([http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_remap_the_Caps_Lock_key_as_another_Control_key](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_remap_the_Caps_Lock_key_as_another_Control_key))

However, after making the changes in either of these two cases I find that holding down caps lock will not have the same effect as holding down the control key (caps lock is eventually ignored if held down for more than one keystroke). 

For instance, if I open a terminal or emacs and type 'asdf' and hit Ctrl-a Ctrl-e (holding down Caps Lock instead of Ctrl), Caps Lock works as Ctrl for the Ctrl-a but then does not take me to the end of the line for Ctrl-e, and instead places the letter 'e' at the beginning of the line.

I wonder if this is a known bug/feature and if anyone has any workarounds? Thanks!

Stephen

---

### Post by hwttdz on 2009-08-28
Try looking at these methods, see if any of them help?

[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

---

### Post by blackandwhitepandabear on 2009-08-29
Thanks - xmacro seems like the best bet... I will give that a try (have to read up on it a bit more).

---

### Post by PGScooter on 2009-08-29
xmacrorec2 is broken in Jaunty and Karmic, as far as I know.

---

