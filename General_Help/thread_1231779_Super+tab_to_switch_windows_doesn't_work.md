---
title: "Super+tab to switch windows doesn't work"
date: 2009-08-04
forum: General Help
---

### Post by nmaster on 2009-08-04
Is the super ("windows") key used for anything?

When I go to System->Preference->Windows to change the window-switching shortcut from Alt+Tab to Super+Tab, nothing changes.  I can still change windows with Alt+tab, but Super+tab does nothing.  I've tried restarting and this doesn't help.  

I kind of just wanted the super key to be used for something, especially since I'll be getting stickers to cover the windows logo to an ubuntu logo.

Any suggestions?

---

### Post by darolu on 2009-08-04
If you have Compiz running you have to edit the shortcuts there; install the compiz configurator with:
```
sudo apt-get install compizconfig-settings-manager
```
(or search it on synaptic)

There are some settings that use "super" as default shortcut key (combined with another), including key ringer (like alt+tab but in a cool ring).

I personally use the "super" key a lot for my custom commands, I set them in compiz settings manager, for example with "super+enter" a terminal pops up, very useful.

---

### Post by nmaster on 2009-08-04
> **darolu said:**
> If you have Compiz running ...

I didn't have compiz running.  It messes with Matlab.  However, I just accidentally typed "compiz" into the terminal.  I guess I didn't realize that the configuration manager was in Preferences.  How do I stop compiz?  I tried "killall compiz" but that doesn't do anything.  

My original question regarding window-switching still holds.

---

### Post by darolu on 2009-08-04
> **neal.m.master said:**
> I didn't have compiz running.  It messes with Matlab.  However, I just accidentally typed "compiz" into the terminal.  I guess I didn't realize that the configuration manager was in Preferences.  How do I stop compiz?  I tried "killall compiz" but that doesn't do anything.  

My original question regarding window-switching still holds.

Also notice the option you are editing (the one in your screnshot) doesn't do the same thing "alt+tab" does, what it does is allow you to move your window around with the mouse, like when you click and drag on the top title-bar.

The easiest way to "kill" compiz is going to system-preferences-appearance (themes) and disable visual effects.

---

### Post by nmaster on 2009-08-04
> **darolu said:**
> Also notice the option you are editing (the one in your screnshot) doesn't do the same thing "alt+tab" does, what it does is allow you to move your window around with the mouse, like when you click and drag on the top title-bar.

The easiest way to "kill" compiz is going to system-preferences-appearance (themes) and disable visual effects.


Oh, I guess I didn't look closely enough.  So I looked in "Keyboard Shortcuts" but using super+tab doesn't change the shortcut.  I can change other ones though.  Is Alt+Tab reserved or something?

---

### Post by nmaster on 2009-08-05
bump.

---

### Post by drs305 on 2009-08-05
In metacity, you can change the command from ALT-Tab to Super-Tab by opening gconf-editor and editing /apps/metacity/global_keybindings/switch_windows.  Replace <Alt>Tab with <Super>Tab.

To open gconf-editor to the correct location:
```

gconf-editor /apps/metacity/global_keybindings/switch_windows

```
Replace <Alt>Tab with <Super>Tab
To reset to  the default, right click the value and select "Unset Key".

(Alt-Tab won't work until reset)

I don't use Compiz in Karmic so I can't tell you if it would retain the setting if you are using Compiz.

---

### Post by nmaster on 2009-08-07
thanks! i don't use compiz either.

---

