---
title: "Bluetooth disconnected after hibernate"
date: 2010-11-21
forum: General Help
---

### Post by ranxerox on 2010-11-21
This problem has existed for me on both 8.04 and 10.04.  I'm using an old IBM ThinkPad T42.  The device in question is a bluetooth mouse manufactured by Kensington.  After a reboot the mouse connects, but after resuming from a hibernate it doesn't.  Many other people have complained about similar issues on a variety of platforms over a period of years.

It's pretty easy to recover using the GUI.  I can use the Bluetooth Preferences panel to remove the old connection for the mouse.  Then the same panel enables me to scan for devices and re-activate the mouse.  This works most of the time, though occasionally it seems to get into a bad state and won't connect without a reboot.

The problem is that this sequence of events is necessary each time I resume from hibernate.  In addition the mouse disconnects sometimes if I just leave the machine for long enough.  Plus, when I'm invoking the Bluetooth Preferences I must use an alternate cursor control device.  It's all a pain.

So I've been trying to find a tool that would reconnect the mouse with the least amount of hassle.  What I found is that the [FONT="Courier New"]hidd[/FONT] utility.  I don't remember for certain whether it was already loaded, I was trying a lot of stuff at the time and it all gets confused, it may be in a [FONT="Courier New"]bluez[/FONT] tool package.

The key commands are:

```

sudo hidd --killall # kill all existing connections
sudo hidd --search  # scan and connect to all devices

```

Of course the latter command will only work if I press the button on the mouse that makes it pair.

So I put these commands into a script and hooked the script to a custom application in the menu bar.  That was a lot simpler than the Bluetooth Preferences sequence.  I just had to click on my custom application icon and a terminal window would come up.  Enter my password for the [FONT="Courier New"]sudo[/FONT] and push the button on the mouse.

Then I wrote a C program to invoke the two commands.  By installing it in [FONT="Courier New"]/usr/local/bin[/FONT], changing its ownership to [FONT="Courier New"]root[/FONT], and setting its [FONT="Courier New"]suid[/FONT] bit I could avoid the whole [FONT="Courier New"]sudo[/FONT] password hassle.  Which meant it didn't need a terminal window.  Not too bad.

I should have left it there but I got carried away.  The [FONT="Courier New"]zenity[/FONT] utility (which *was* already loaded on my system) can put up a progress box on the screen and incidentally show a message reminding me to push the button on the mouse.  So I modified my C program to push out progress messages and status and piped that into [FONT="Courier New"]zenity[/FONT].  Then I attached the script instead of the utility to my custom application icon.

Finally, I connected the script to a keyboard shortcut.  That's even easier.  After I resume from hibernate and login I can just hit <Ctrl><Alt>B, the [FONT="Courier New"]zenity[/FONT] progress panel pops up, and I push the button on the mouse.  That's as easy as I've been able to make it, and it's painless enough to actually use the mouse.

I'm attaching an archive with three files:

[LIST]
[*]C program
[*]Build script
[*]Shell script
[/LIST]

The build script has to be run via [FONT="Courier New"]sudo[/FONT] in order to install the C program properly.  The application thus created will run in two modes.  With no arguments it prints a message about pushing the button and then [FONT="Courier New"]hidd[/FONT] prints some messages.  With the single argument [FONT="Courier New"]"zenity"[/FONT] it will generate output that can be piped into [FONT="Courier New"]zenity --progress[/FONT].  The latter is how it is used in the shell script.

I'm posting all this in case someone else can use it.  And because the solution tickles me.  I can't decide whether it's an inspired hack or a horrible kludge.  But it works, for me, for the moment, and that's got to be good enough.

If you can't be good, be good at being bad.  ;)

---

