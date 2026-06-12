---
title: "Force Quit Keybaord short cut?"
date: 2011-07-06
forum: General Help
---

### Post by conradin on 2011-07-06
Im looking for the force quit keyboard shortcut. Like XKill or what ever the force quit in Gnome panel is. Anything which will kill a misbehaving application which has locked up the mouse.

---

### Post by madebyjordan on 2011-07-06
I'd also like to know. I came across this recently although the solution is fairly old so I'd like to know if there are any better methods - [http://www.linuxforums.org/forum/ubuntu-linux/74391-ctrl-alt-delete.html#post704064](http://www.linuxforums.org/forum/ubuntu-linux/74391-ctrl-alt-delete.html#post704064)

---

### Post by conradin on 2011-07-06
Hey, Thats good enough for me!
Heres what I did:

```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>x"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "xkill"

```

so when I press ctrl+alt+x an x kill icon appears and I can point & click to kill a process.

---

### Post by scu-ba-de-buntu on 2011-08-21
Why is this not part of the standard dist?

---

### Post by 3rdalbum on 2011-08-21
> **conradin said:**
> Im looking for the force quit keyboard shortcut. Like XKill or what ever the force quit in Gnome panel is. Anything which will kill a misbehaving application which has locked up the mouse.

If you can't move the mouse, then you can't use Xkill to select the window you want to kill.

Also, if you can't move the mouse, chances are that your X server has crashed, not just one of the programs.

The keyboard combination Alt-Printscreen-K will restart the X server, killing all open GUI programs in the process.

---

