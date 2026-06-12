---
title: "Intermittent black screen on boot"
date: 2011-10-13
forum: General Help
---

### Post by chrisk0 on 2011-10-13
I have an eeePC 701 4gig surf, and last December I updated it to Xubuntu Maverick Meerkat. It mostly runs great.

But starting around May I noticed that it would sometimes have screen problems when booting up - no desktop, no mouse pointer, just a black screen and the indicator lights for power, and the disk indicator light flickering. When this happens, I can turn the wireless on and off with the proper hotkey, but nothing else has an obvious effect.

Generally I can get it to come back by holding down the power key for a few seconds to shut the machine down and booting again, but it's happening a bit more frequently, so I thought I'd ask for tips in solving or troubleshooting the issue, as I don't really even know where to look to see what's going wrong. Thank you for any tips you can provide, or questions you can ask.

---

### Post by ultrageeky on 2011-10-13
Check your home directory for the following files:

[LIST]
[*]xinitrc
[*].xserverrc
[*].xsession
[/LIST]
You might need to change your view settings to display hidden (dot) files.

Delete them if they're present. Here's a command line way to rename them:

```
sudo mv ~/.xinitrc ~/.xinitrc.bckxyz; sudo mv ~/.xserverrc ~/.xserverrc.bckxyz; sudo mv ~/.xsession ~/.xsession.bckxyz
```

By renaming them you can restore should you need to. If you do need to restore them, run this in a terminal:

```
sudo mv ~/.xinitrc.bckxyz ~/.xinitrc; sudo mv ~/.xserverrc.bckxyz ~/.xserverrc; sudo mv ~/.xsession.bckxyz ~/.xsession
```

Those files are used to enable virtual desktop sessions and to configure a specific user's own desktop without affecting the global desktop settings. Sometimes they become corrupted and cause problems. They're not essential for people who do not use multiple virtual desktop sessions simultaneously or for those who do not have multiple login user names.

If you want to recreate one or more of those files, just create a new text file with the relevant name and add this text into it:

```
#!/bin/sh
# Each line here tells Xorg to load a specific desktop environment when a desktop session is created.
# Remove the hash sign (#) to uncomment the instruction you want Xorg to execute.
# Prepend a hash sign to any line to comment it out.
# Only one line should be uncommented.
# Only uncomment an instruction if you have the required environment installed
# KDE is uncommented by default

# exec afterstep # AfterStep
# exec blackbox # Blackbox
# exec enlightenment # Enlightenment
# exec fluxbox # Fluxbox
# exec startfluxbox # Fluxbox
# exec fvwm # FVWM
# exec fvwm2 # FVWM2
# exec gnome-session # GNOME
# exec icewm # IceWM
# exec ion #
# exec mwm # Motif
# exec openbox # Openbox
# exec openbox-session # Openbox
# exec pekwm
# exec qvwm # qvwm
# exec /usr/bin/ratpoison
exec startkde # KDE
# exec startlxde
# exec startxfce4 # XFce 4
# exec wmaker # WindowMaker
# exec xfce # XFce 3
# exec xterm
# ...or another installed Window Manager

```

Because you are using Xubuntu which uses the XFCE desktop environment you will need to comment out "
exec startkde # KDE" and uncomment (remove the hash sign) from "# exec startxfce4 # XFce 4 "

The above instructions come from this desktop recovery guide at [JournalXtra]("http://journalxtra.com/2011/08/getting-your-desktop-back-the-almost-definitive-guide").

---

### Post by chrisk0 on 2011-10-13
Thank you very much for your answer.

None of those files are in my home directory, /home/chrisk . The only hidden files starting with .x there are:
.Xdefaults
.xscreensaver
.xsession-errors
.xsession-errors.old

Would xsession-errors have anything relevant, and if so, how would I be able to find it there?

---

### Post by ultrageeky on 2011-10-13
You're welcome.

There might be something in .xsession-errors but it will be an incredibly long file. Delete it then wait for the problem to recur before checking the file for any errors around the time of the problem's occurrence.

I would also create the three files I mentioned last time and check the screen saver is disabled, maybe it's not properly switching off when the computer receives input.

Disable any desktop effects like Compiz and Emerald (if installed).

Next time the problem occurs try pressing Ctrl or Esc or Ctrl+F1 and let us know whether any of those keys being pressed causes anything to show on the screen.

---

