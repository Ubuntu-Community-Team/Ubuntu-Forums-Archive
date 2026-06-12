---
title: "Change default calculator"
date: 2010-02-20
forum: General Help
---

### Post by beartard on 2010-02-20
Ubuntu uses gcalctool as the default calculator application.  When I press the calculator button on my keyboard, it opens gcalctool.  Is there a way to change this to open qalculate instead?  I know I can set another keyboard shortcut for it, but having it pop up when I hit the calculator key would be nice.

---

### Post by The Toxic Mite on 2010-02-20
I don't think there's any software for the re-mapping of keys. I'm not on my Ubuntu box right now, so I'll check back later.

---

### Post by pi/roman on 2010-02-20
Enter the following code in terminal and it will open up your .Xmodmap file in your home directory and print the keycode number for your calculator key. Copy the keycode up to and including the equal sign and paste it into your .Xmodmap file. When you reboot your calculator key will be stripped of identifiers that make the shortcut work.  Then you can make a new shortcut to qalctool and use the same key and it will only work for qalctool.
```
gksudo gedit ~/.Xmodmap | xmodmap -pke | grep -i calc | grep -o '^.*='
```You can revert the key back to normal by opening .Xmodmap and deleting the keycode command and rebooting:
```
gksudo gedit .Xmodmap
```

---

### Post by vamped on 2010-07-01
I think the easiest solution is to turn the original gcalctool file into a link to qalculate.

```
sudo mv gcalctool gcalctool_original
sudo ln -sT /usr/bin/qalculate-gtk /usr/bin/gcalctool
```

It works instantly. To undo, you would just:

```
sudo mv /usr/bin/gcalctool_original /usr/bin/gcalctool
```

---

### Post by swwing17 on 2010-08-02
I just tried:
```
sudo mv gcalctool gcalctool_original
```

and got:
*mv: cannot stat `gcalctool': No such file or directory*

I know gcalctool is installed.  Any suggestions?

---

### Post by swwing17 on 2010-08-02
The instructions in the previous posts didn't work for me, so I went into (in Linux Mint) Menu>"Keyboard Shortcuts", clicked "Add".  In the "Name" box I typed "Launch Qalculate", and in the "Command" box I put */usr/bin/qalculate-gtk*.  I clicked "Apply".  I then (still in Keyboard Shortcuts) scrolled to "Launch Qalculate", clicked on the "Shortcut" column where it said "Disabled", so it said "New shortcut...", and pressed the keyboard key I want to assign to launch it.  Closed "Keyboard Shortcuts", and it works now.

I hope this helps.

---

### Post by luigi_mb on 2010-08-02
> **swwing17 said:**
> I just tried:
```
sudo mv gcalctool gcalctool_original
```

and got:
*mv: cannot stat `gcalctool': No such file or directory*

I know gcalctool is installed.  Any suggestions?

Do this first:

```
cd /usr/bin
```


/luigi

---

### Post by meng1usa on 2010-09-25
I have same problem, so the following procedure should fix your problem:

1. find the key value of your calculator key in system--preference--keyboard shortcut

2. in terminal, type in following command
```
gconf-editor
```

Go under apps/metacity , you should see

global_keybindings and keybinding_commands.

If you click on global_keybindings, on the right pane you will find some entry for commands, like: run_command_1, run_command_2, etc. These have to be filled up with the relevant keysym for your key (like: XF86Play, XF86MyComputer, etc. use xev to see).
Then you can assign the matching command (or script) on the other row, under keybinding_commands.

you can find more details here
[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

---

