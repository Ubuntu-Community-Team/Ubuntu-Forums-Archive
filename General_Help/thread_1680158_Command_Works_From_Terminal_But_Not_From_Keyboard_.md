---
title: "Command Works From Terminal But Not From Keyboard Shortcut"
date: 2011-02-02
forum: General Help
---

### Post by ooter37 on 2011-02-02
I would like to make a keyboard shortcut to execute the following command:

```
/usr/bin/xdotool key XF86MonBrightnessDown
```

The command, when run from a terminal, works perfectly. However, when run via a keyboard shortcut, the command fails to execute.

I am very new to linux and I would really appreciate it if someone could explain how I can execute my command with a keyboard shortcut.

I am running Ubuntu 10.10 Netbook Edition with Unity-2d.

Thank you

---

### Post by slooksterpsv on 2011-02-02
Funny, I was just playing with keyboard shortcuts today, in XFCE 4.8 - making volume changing and shortcuts to terminal, etc.

I'd create a script in your home directory, give it executable rights, and have your shortcut key execute that script. Try that, see if that works.

---

### Post by sisco311 on 2011-02-02
Or try to run the command in a shell:
```
sh -c "/usr/bin/xdotool key XF86MonBrightnessDown"
```

---

### Post by ooter37 on 2011-02-02
Thank you for the quick replies. I tried each suggestion but neither worked. I did have some success by executing the following script:
```
/usr/bin/xdotool key XF86MonBrightnessDown
```
from the command:
```
gnome-terminal -e "bash /home/derek/brightnessdown"
```

The problem with that workaround is that it pops up a terminal for a second and adds an annoying 1-2 second delay each time I execute my shortcut.

---

### Post by Rebelli0us on 2011-11-18
Same problem here, I made a simple keyboard shortcut to raise/lower the sound volume. It works fine in Terminal (and Alt+F2) but not in Keyboard Shortcuts.

xdotool key XF86AudioRaiseVolume


Help!

---

### Post by killermist on 2011-11-18
> **ooter37 said:**
> 
```
gnome-terminal -e "bash /home/derek/brightnessdown"
```

The problem with that workaround is that it pops up a terminal for a second and adds an annoying 1-2 second delay each time I execute my shortcut.
Can you drop the "gnome-terminal -e" part so that it doesn't spawn the terminal program and then execute bash to execute the script and instead just executes the script with bash?
What I mean is, launching the terminal program is unnecessary (I think) because you don't need to see any output or interact in any way, you just want the command executed.
If your script has the proper
```
#!/bin/bash
```
as the first line, it should be able to directly invoke the script (which is executable, I hope) instead of having to invoke bash with the script as a parameter.

---

### Post by Rebelli0us on 2011-11-19
Thank you. Is this an answer to my question above?

---

### Post by stinkeye on 2011-11-19
> **Rebelli0us said:**
> Thank you. Is this an answer to my question above?
Try using as the command in startup applications
```
xdotool key **--clearmodifiers** XF86AudioRaiseVolume
```
When running from a terminal your not holding down any keys,
where as when setting the command to a keyboard shortcut 
your more than likely holding down alt, shift or ctrl or a combo of these.


From **man xdotool**
> CLEARMODIFIERS
 Any command taking the --clearmodifiers flag will attempt to clear any active input modifiers during the command and restore them afterwards. 

 For example, if you were to run this command: 
 xdotool key a 

 The result would be 'a' or 'A' depending on whether or not you were holding the shift key on your keyboard. Often it is undesirable to have any modifiers active, so you can tell xdotool to clear any active modifiers. 

 The order of operations if you hold shift while running 'xdotool key --clearmodifiers a' is this: 
1. Query for all active modifiers (finds shift, in this case)
2. Try to clear shift by sending 'key up' for the shift key
3. Runs normal 'xdotool key a'
4. Restore shift key by sending 'key down' for shift

---

### Post by Rebelli0us on 2011-11-19
> **stinkeye said:**
> Try using as the command in startup applications
```
xdotool key **--clearmodifiers** XF86AudioRaiseVolume
```
When running from a terminal your not holding down any keys,
where as when setting the command to a keyboard shortcut 
your more than likely holding down alt, shift or ctrl or a combo of these.


From **man xdotool**

Thank you. That works but also trashes the OS (start menu, guest OS, etc.) forcing a reboot every time you use it. ouch!

There's another applet that can do the same

```
xte "key XF86AudioRaiseVolume"
```

found it in Ubuntu software centre under "xautomation". But it has the same problem, works form terminal but not as a keyboard shortcut.

What do you mean "When running from a terminal you're not holding down any keys"?You **are** pressing the Enter key.

Any ideas? We need a simple shortcut to adjust the sound volume for people that don't have Volume buttons on their keybd!!!

---

### Post by stinkeye on 2011-11-19
It means your modifier keys (ctrl alt Super or shift)are being registered along with the XF86AudioRaiseVolume key.
Your holding down a modifier key while sending a command to initiate another key.

What keys are you using for the shortcut?

If I use ctrl+shift+u as the shortcut, this command works in keyboard shortcuts.
```
sh -c "xdotool key --clearmodifiers XF86AudioRaiseVolume && xdotool keyup ctrl+shift"
```

I found the original command sometimes left the modifier keys in the down positon.
The **&& xdotool keyup ctrl+shift** part makes sure they're returned to up.

[COLOR="Red"]EDIT[/COLOR]I just reread your previous post.
> Any ideas? We need a simple shortcut to adjust the sound volume for people that don't have Volume buttons on their keybd!!!
Cant you just change the "volume up" shortcut key in the sound and media heading.

---

### Post by dcstar on 2011-11-19
Perhaps this is relevant:

[http://ubuntuforums.org/showpost.php?p=10546992&postcount=86](http://ubuntuforums.org/showpost.php?p=10546992&postcount=86)

---

### Post by Rebelli0us on 2011-11-20
> **stinkeye said:**
> It means your modifier keys (ctrl alt Super or shift)are being registered along with the XF86AudioRaiseVolume key.
Your holding down a modifier key while sending a command to initiate another key.

What keys are you using for the shortcut?

If I use ctrl+shift+u as the shortcut, this command works in keyboard shortcuts.
```
sh -c "xdotool key --clearmodifiers XF86AudioRaiseVolume && xdotool keyup ctrl+shift"
```

I found the original command sometimes left the modifier keys in the down positon.
The **&& xdotool keyup ctrl+shift** part makes sure they're returned to up.

[COLOR="Red"]EDIT[/COLOR]I just reread your previous post.

**Cant you just change the "volume up" shortcut key in the sound and media heading.**

Yes that works. I thought of changing those but I didn't because I assumed that it would disable the actual volume buttons on keyboards that have them. What do you think? I don't have a multimedia kybd to test this.

---

### Post by stinkeye on 2011-11-20
> **Rebelli0us said:**
> Yes that works. I thought of changing those but I didn't because I assumed that it would disable the actual volume buttons on keyboards that have them. What do you think? I don't have a multimedia kybd to test this.
Yes it will as well as the volume up  button on headphones.

---

### Post by Rebelli0us on 2011-11-21
> **stinkeye said:**
> Yes it will as well as the volume up  button on headphones.

It also messed up the sound volume keys on my Wii Remote, so don't do it folks.

So we still have no solution. Linux has no equivalent to Windows' sendkeys? I uninstalled *xdotool* for being lethal to gnome.

```
xte "key XF86AudioLowerVolume"
```

works in terminal but not as kbd shortcut.

I looked at the "sh -c" thing you mentioned above, some kind of command interpreter, does it exit when done?

---

### Post by stinkeye on 2011-11-21
> **Rebelli0us said:**
> It also messed up the sound volume keys on my Wii Remote, so don't do it folks.

So we still have no solution. Linux has no equivalent to Windows' sendkeys? I uninstalled *xdotool* for being lethal to gnome.

```
xte "key XF86AudioLowerVolume"
```

works in terminal but not as kbd shortcut.

I looked at the "sh -c" thing you mentioned above, some kind of command interpreter, does it exit when done?
What tripe!
If you have a peripheral device that has a volume up key
open the keyboard shortcut for **volume up**, double click to set a short cut, press the volume up key and it will be set back to **Audio raise volume**

The original command will work
```
xdotool key XF86AudioRaiseVolume
```
It's just a matter of using the right keyboard shortcuts.
eg alt+pageup works fine.

---

### Post by Rebelli0us on 2011-11-22
> **stinkeye said:**
> What tripe!
If you have a peripheral device that has a volume up key
open the keyboard shortcut for **volume up**, double click to set a short cut, press the volume up key and it will be set back to **Audio raise volume**

The original command will work
```
xdotool key XF86AudioRaiseVolume
```
It's just a matter of using the right keyboard shortcuts.
eg alt+pageup works fine.

What do you mean the *right keyboard shortcuts*? I used Winkey+up/down, it changed the volume but then gnome got disabled, lost access to start menu, real ugly, I had to reset.

---

### Post by stinkeye on 2011-11-22
> **Rebelli0us said:**
> What do you mean the *right keyboard shortcuts*? I used Winkey+up/down, it changed the volume but then gnome got disabled, lost access to start menu, real ugly, I had to reset.

A modifier key that doesn't affect the functioning of the XF86AudioRaiseVolume key.
Super ctrl and shift all affect it. Alt does not.

---

### Post by Rebelli0us on 2011-11-25
I decided that it's simpler to assign commands:

```
amixer set Master 5+
```

a (minus)- to lower volume, and 0 to mute.

System "Sound Preferences" *Output* panel shows the volume go up to 100% but no more, though you can get more volume by using the mouse to drag the little thumb beyond 100% -- what's up with that?

---

