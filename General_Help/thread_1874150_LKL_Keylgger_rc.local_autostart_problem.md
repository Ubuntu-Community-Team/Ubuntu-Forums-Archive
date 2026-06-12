---
title: "LKL Keylgger rc.local autostart problem"
date: 2011-11-02
forum: General Help
---

### Post by syngress on 2011-11-02
Hello. I try to setup LKL Keylogger on one of my eeepc laptop with Lubuntu on board. Problem is that i cannot setup autostart from **/etc/rc.local** 

I try to add:

```

lkl -l -k /my/lkl/keymaps/cat/us_km -o my/folder/with/log.txt
exit 0

```

after system reboot - nothing .. don't start, don't work - syslog clean. When i try to run rc.local from terminal, everything work's like a charm !! :(

Please assist ..

---

### Post by amjjawad on 2011-11-03
Hi there,

Have a look at my signature (Lubuntu One Stop Thread) - Section C

:)

---

### Post by syngress on 2011-11-03
> **amjjawad said:**
> Hi there,

Have a look at my signature (Lubuntu One Stop Thread) - Section C

:)

Thanks. Still nothing.
I make a file (lkl.desktop) and copy it to ~/.config/autostart/

```

[Desktop Entry]
Name=URxvt
Comment=Opens a terminal with UTF-8 and 256 colors support
Encoding=UTF-8
Exec=lkl -l -k /my/folder/with/keymaps/us_km -o /myfolder/with/file/log.txt
Icon=gksu-root-terminal
StartupNotify=true
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Application;System;
NoDisplay=true

```

Then i go to Session Manager and autostart URxvt
Reboot
Nothing ... :confused:

---

### Post by amjjawad on 2011-11-03
What release of Lubuntu are you using?

---

### Post by syngress on 2011-11-03
> **amjjawad said:**
> What release of Lubuntu are you using?

Latest release.

---

### Post by amjjawad on 2011-11-04
> **syngress said:**
> Thanks. Still nothing.
I make a file (lkl.desktop) and copy it to ~/.config/autostart/

```

[Desktop Entry]
Name=URxvt
Comment=Opens a terminal with UTF-8 and 256 colors support
Encoding=UTF-8
Exec=lkl -l -k /my/folder/with/keymaps/us_km -o /myfolder/with/file/log.txt
Icon=gksu-root-terminal
StartupNotify=true
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Application;System;
NoDisplay=true

```Then i go to Session Manager and autostart URxvt
Reboot
Nothing ... :confused:

Does your application show up on the Menu?
If yes, under what category?

If not, edit your file:

```

[Desktop Entry]
Name=URxvt
Comment=Opens a terminal with UTF-8 and 256 colors support
Encoding=UTF-8
Exec=[COLOR=Blue]**lkl -l -k /my/folder/with/keymaps/us_km -o /myfolder/with/file/log.txt**[/COLOR]
Icon=gksu-root-terminal
StartupNotify=true
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=**[COLOR=Blue]Application;System[/COLOR]**;
[COLOR=Red]**#**[/COLOR]NoDisplay=true

```

The lines in BLUE = I'm not sure about that specially Exec. It should be a command not a path as far as I know. Perhaps I'm wrong though.
For Categories, try to use "Settings".

The one in red, I'm sure about.

After you make sure your application does show up on the Menu, try to open it and see if it works. Then, we can set it to autostart.

---

