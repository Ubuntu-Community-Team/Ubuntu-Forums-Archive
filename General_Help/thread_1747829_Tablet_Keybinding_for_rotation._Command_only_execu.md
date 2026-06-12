---
title: "Tablet Keybinding for rotation. Command only executed 2 times"
date: 2011-05-03
forum: General Help
---

### Post by WG- on 2011-05-03
Okay since GNOME3 my keybinding to execute my [rotate.sh](http://ubuntuforums.org/showthread.php?t=1587413) bash script won't work anymore.

This is what I have done to try to get it working:
[LIST][*]Opening the configuration editor. 
Goto: "apps/metacity/keybinding_command/command_1" and set it to "bash Desktop/rotate.sh"[/code]
Goto: "apps/metacity/global_keybindings/run_command_1" and set it to "Mod4 + 6". Mod4+6 is as far as I know the rotate button on my tablet img: [http://idhp.net/wp-content/uploads/2009/04/idhp_pic-122.jpg](http://idhp.net/wp-content/uploads/2009/04/idhp_pic-122.jpg), it is the button above the 'key' button.
[*]Installing 'xbindkeys' and 'xbindkeys-config'. I started xbindkeys-config and added the command "bash Desktop/rotate.sh" then using the "get key" button I pressed my tablet rotate button. This resulted in the key "Mod4 + 6 | m:0x40 + c:15". Pressing the rotate button on my tablet then worked for 2 times (strange?). Rotating 180 degrees and rotating 180 degrees back. After pressing it 2 times it does not work anymore. If you press "apply" it works again (for 2 times).[/LIST]

Because it works 2 times I thought it might be possible there was a flaw in my rotate.sh script. However binding the rotate.sh to another key "8" for example did function perfectly. 

Another curious thing is that after the 2 times I rotated pressing my rotate button returns a "6".

My rotate.sh script
```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
    xrandr -o inverted
    xsetwacom set "Serial Wacom Tablet" Rotate HALF
    xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
    xsetwacom set "Serial Wacom Tablet touch" Rotate HALF
else
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet" Rotate None
    xsetwacom set "Serial Wacom Tablet eraser" Rotate None
    xsetwacom set "Serial Wacom Tablet touch" Rotate None
fi
```

Who can help me solve this?

---

### Post by WG- on 2011-05-05
No one?

---

### Post by WG- on 2011-05-08
I'm getting desperate here :(

---

