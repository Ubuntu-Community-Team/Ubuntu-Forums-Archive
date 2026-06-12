---
title: "Issues with my xfce4-keyboard-shortcuts.xml file"
date: 2009-07-23
forum: General Help
---

### Post by Lostin60's on 2009-07-23
Why is it that some of the key assignments in xfce4-keyboard-shortcuts.xml work, while others do not?  For instance, ```
<property name="&lt;Alt&gt;Tab" type="string" value="cycle_windows_key"/>
<property name="&lt;Alt&gt;F4" type="string" value="close_window_key"/>
<property name="&lt;Alt&gt;&lt;Shift&gt;Tab" type="string" value="cycle_reverse_windows_key"/>
```all work fine, but```
 <property name="&lt;Alt&gt;&lt;Control&gt;End" type="string" value="move_window_next_workspace_key"/>
<property name="&lt;Control&gt;F1" type="string" value="workspace_1_key"/>
<property name="&lt;Control&gt;&lt;Shift&gt;&lt;Alt&gt;Right" type="string" value="move_window_right_key"/>
```doesn't work at all?

I am considering customizing my default keymap, which is, I believe, usr/include/linux/input.h.  There are things from my xfce4-keyboard-shortcuts.xml I want to use, but some of those things don't work. Also I can't use them, as written, in xfce4-keyboard-shortcuts.xml. 

My multi-media keys, as well as "special" keys (search, home, calculator, etc.) are listed in usr///input.h, but they don't work either.  

I have googled, read various "man" files, and studied several related files.  I am reasonably certain that I can build a keymap from scratch, if needs be. 

I have run "showkey", "dumpkeys", and "xev", so I have keycodes, scancodes, etc. However I am curious as to why "showkey and "dumpkeys" agree with usr///input.h, while xev agrees with nothing.  Which brings up a stumbling block for me. I want to map my mouse buttons to keystrokes, but only "xev" will show the scancode/keycode for the mouse, but has every thing else wrong, so I am sure the mouse info is also wrong.  

I am thinking I can use button_1, button_2, and so on in this manner ```
<property name="&lt;Alt&gt;Winl&gt;Right" type="string" value="button_3"/>
``` I aven't figured out a dbl-click yet.  Maybe typing the info in the "name" field twice.  I will look for the terminal layout and see how dbl-tab is handled there.

If anyone has any ideas or comments I will be most grateful to hear them.
[COLOR="White"]aa[/COLOR]

---

