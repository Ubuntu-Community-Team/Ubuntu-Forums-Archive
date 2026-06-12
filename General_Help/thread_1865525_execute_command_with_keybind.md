---
title: "execute command with keybind"
date: 2011-10-20
forum: General Help
---

### Post by Troubadix-der-Barde on 2011-10-20
Hi all,

I got a keyboard-backlight, wich now on 11.10 by default is deactivated. It's able to activate it with ```
echo 1 | tee -a /sys/devices/platform/sony-laptop/kbd_backlight
```

I would prefer to set a keybind for that. So I wrote in .config/openbox/rc.xml ```
<keyboard>
  .......
    <keybind key="Help">
      <action name="Execute">
        <execute>/bin/sh -c 'echo 1 | tee -a /sys/devices/platform/sony-laptop/kbd_backlight'</execute>
      </action>
    </keybind>
  .......
</keyboard>
```but that doesn't seem to work.

I got the write permission for that file and the solution above works very well on Archlinux. What am I making wrong here?

I'm using ubuntu 11.10 with xfce.

Thanks and greets.

---

### Post by gsmanners on 2011-10-20
Well, the problem there is that you're using xfwm rather than openbox. If that were my problem, I'd make a bash script somewhere with this in it:

```
echo 1 | tee -a /sys/devices/platform/sony-laptop/kbd_backlight
```

And then set the script as the "Command" in the Settings / Keyboard / Application Shortcuts dialog.

---

### Post by Troubadix-der-Barde on 2011-10-20
Yes, that´s the way and you are the man. Thank you very much.

Didn´t know, that I don´t use openbox.

---

