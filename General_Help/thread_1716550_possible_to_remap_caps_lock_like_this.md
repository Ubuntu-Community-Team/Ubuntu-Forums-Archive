---
title: "possible to remap caps lock like this?"
date: 2011-03-28
forum: General Help
---

### Post by supermooshman on 2011-03-28
[**here we go** (lifehacker)]("http://ca.lifehacker.com/5784557/how-to-turn-caps-lock-into-a-search-key-on-your-mac-redux")
seems like an interesting way of working (especially since I never use caps lock - well I use it to enter a wrong password)

Is this possible with ubuntu
... well [**everything**]("http://www.yousaytoo.com/diy-cat-feeder-powered-by-ubuntu-linux-cd-rom-tray/139952") is possible with ubuntu, but how do I actually do it?

---

### Post by anglican on 2011-03-29
> **supermooshman said:**
> [**here we go** (lifehacker)]("http://ca.lifehacker.com/5784557/how-to-turn-caps-lock-into-a-search-key-on-your-mac-redux")
seems like an interesting way of working (especially since I never use caps lock - well I use it to enter a wrong password)

Is this possible with ubuntu
... well [**everything**]("http://www.yousaytoo.com/diy-cat-feeder-powered-by-ubuntu-linux-cd-rom-tray/139952") is possible with ubuntu, but how do I actually do it?It's very easy on xubuntu, probably the same (or similar) on other desktop environments. I choose ```
Settings->Xfce 4 Settings Manager
```from the Applications menu. Then "Keyboard" in the settings manager and the "Application Shortcuts" tab. Select "+Add" and enter e.g. /usr/bin/firefox in the "Command" box and press the Caps-Lock key. Quit and you're done, Caps-Lock will now start the firefox browser when pressed.

---

### Post by supermooshman on 2011-03-29
cool,
I'll see if it is the same with ubuntu once I get home.

By doing this, would the caps lock still be caps lock? 
ie would I get a firefox window + GET ALL UPPERCASE?

Thanks

---

### Post by Krytarik on 2011-04-04
> **supermooshman said:**
> 
By doing this, would the caps lock still be caps lock? 
ie would I get a firefox window + GET ALL UPPERCASE?

LOL:D Yeah, it would do so!

I picked up your idea and managed to turn the CapsLock key into a real Search key, here it is:

~/.Xmodmap:
```

keycode 66 = XF86Search

```- "System -> Preferences -> Keyboard -> Layout -> Options -> CapsLock key behavior" => "CapsLock is disabled"

- "System -> Preferences -> Keyboard Shortcuts -> Desktop -> Search" => "Shift+XF86Search"

[COLOR=Blue]optional: add a keyboard shortcut for Ctrl+F => Ctrl+XF86Search
[/COLOR] 
- needed package: "lineakd"

- Compiz:
```
xsendkeycode 66 0; xsendkeys Control+f
```- 'Keyboard Shortcuts':
```
sh -c "xsendkeycode 66 0; xsendkeys Control+f"
```Sorry that it's not *that* detailed as usual. If you have questions, just ask.

Greetings.

PS: Unfortunately, I didn't manage so far to affect the key also at the console, generally it should work the way I set it up.
Also, I didn't manage so far to modify the key system-wide for X incl. GDM, because
1.) GDM apparently doesn't respect any settings made in the "Keyboard" preferences
2.) usual system-wide "/etc/X11/Xmodmap" isn't respected anymore by default, and even running it manually through "/etc/X11/Xsession" doesn't work

---

