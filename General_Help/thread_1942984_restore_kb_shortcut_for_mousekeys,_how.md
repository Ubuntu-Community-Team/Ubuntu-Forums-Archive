---
title: "restore kb shortcut for mousekeys, how?"
date: 2012-03-18
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-18
Among the many dangerous features Canonical wisely decided to eliminate to save the poor stupid users from themselves was a keyboard shortcut to toggle mousekeys. After all it is obvious people could easily accidentally hold down left shift, left alt, and num-lock at the same time and then be forced to use the dreaded top row to enter numbers. After all it is so easy for the people who need this function to navigate the to the proper dialogue that is only four layers deep in the MOUSE DRIVEN menu and make 4 more MOUSE CLICKS after they get there to toggle the thing. How much easier could it be?

Anyway, does anyone know how to restore a keyboard shortcut to toggle this? If you know the command syntax to do it from the command line, I can use that to make a keyboard shortcut to run a script to toggle it even if it has to be two different commands to turn it on and to turn it off. Google only knows methods that used to work before Ubuntu was improved.

---

### Post by stinkeye on 2012-03-18
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11573466&postcount=3")

---

### Post by Dreamer Fithp Apprentice on 2012-03-19
Thank you. That's strange. On Oneiric with Mate I do NOT have the menu choices alluded to in that post. I looked real hard in every subdirectory of the menu. I do not have anything that looks like that dialogue that comes up under any of the halfway likely seeming headings. You'd think the sane place to put an option to use a keyboard shortcut to toggle mousekeys would have been there in the same tab that enabled mousekeys if it wasn't placed very early in the boot process like onboard and high contrast color options are. So maybe I need to install something. Does anybody know what? Or maybe I have the program but just not the GUI wrapper. I don't care about the GUI wrapper if anybody has any idea what the command would be. For that matter I don't even have to have a command or GUI to enable the hot keys if I just had commands to turn on and off Mousekeys. That would actually be even better. With those it is trivial to make a hot key. I delayed responding a bit because I kept thinking I must be missing something obvious, but it isn't in my menu. Maybe it changed from 11.04 to 11.10 or maybe I've uninstalled something it was a part of.

Thanks for the response anyway. If anyone can shed any more light on this I'd appreciate it.

---

### Post by stinkeye on 2012-03-19
Try 
```
gsettings set org.gnome.desktop.a11y.keyboard mousekeys-enable true
```


Here's a toggle script.
```
#!/bin/bash


STATUS=$(gsettings get org.gnome.desktop.a11y.keyboard mousekeys-enable) #Are mousekeys on (true or false)

     if [ "$STATUS" == "true" ]
         then
             gsettings set org.gnome.desktop.a11y.keyboard mousekeys-enable false 
             
             notify-send -i  "/usr/share/icons/gnome/48x48/devices/keyboard.png" "                    Mousekeys OFF"
             echo "Mousekeys are OFF"
         
         else
             gsettings set org.gnome.desktop.a11y.keyboard mousekeys-enable true
             
             notify-send -i  "/usr/share/icons/gnome/48x48/devices/keyboard.png" "                    Mousekeys ON"
             echo "Mousekeys are ON"
         
fi
done

```

---

### Post by Dreamer Fithp Apprentice on 2012-03-19
Thanks! That didn't work for me but it was suggestive enough to give me ideas where to look and what to experiment with. For others who want to do this and are running Oneiric with Mate the commands to turn MouseKeys on and off are:

on:
```
mateconftool-2   --type   boolean   --set /desktop/mate/accessibility/keyboard/mousekeys_enable true
```and

off:
```
mateconftool-2   --type   boolean   --set /desktop/mate/accessibility/keyboard/mousekeys_enable false
```Anybody looking for similar commands should start with the GUI invoked by the command:
```
mateconf-editor
``` and apply analogy, reason, and experiment to what you find out from it. The  Edit,Copy_Key function is invaluable. One caveat: Sometimes the wrong syntax will still work to turn some function OFF because you essentially broke something, which can be misleading if you assume that because it worked to turn something off, it was correct and the opposite should turn it on.  In this case for instance in the "off" command if you put in the wrong type, string for example instead of boolean, ANY value will turn it off, but only the correct command will turn it on.

Stinkeye, I've written toggle scripts of various sorts but yours looks appreciably more elegant and uses a syntax I didn't know, so I will profit from studying and adapting it. Thanks.

---

