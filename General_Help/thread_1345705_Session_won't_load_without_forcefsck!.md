---
title: "Session won't load without forcefsck!"
date: 2009-12-04
forum: General Help
---

### Post by JohnMoriarty on 2009-12-04
My PC (amd64, Karmic) boots up fine to the login screen then when I attempt to login it starts to load the session (the screen resizes/changes resolution and the sound effect starts) and then the X appears to reset and I find myself back at the login screen. The same problem occurs with Gnome and Gnome failsafe sessions, but xterm session load fine. 

The weird bit.
From xterm I use 'sudo touch /forcefsck' and reboot and the it all comes back and works fine; session loads without any problem. Next time I reboot same problem starts all over again.

How do I go about working out what is going wrong?

(Had to replace the monitor the other day, and I've got rid of xorg.conf to make the refresh rate work, but should this cause any problem?)

Thanks

---

### Post by ajgreeny on 2009-12-04
Can you try a new user and see if that starts OK.  If it does then it points to something in your configuration for your own first user, perhaps the display or maybe something else entirely, but you will need to try all possibilities.

I don't see why it should be needed any more with karmic, but try also booting to recovery mode and running **xfix** from the menu that appears.

---

### Post by JohnMoriarty on 2009-12-04
ajgreeny, thanks. I've created a new user which appears to have no difficulty logging on (I've tried a couple of boot cycles). I presume this means that something in my normal profile is getting corrupted?

Tried to try the **xfix** from recovery mode, but there isn't an **xfix** in the menu that appears for me!

What now?

John

---

### Post by JohnMoriarty on 2009-12-04
I've just noticed that when I do get a good login (ie after fsck has run on boot up) the volume is reset to mute. Could this be an indication of which file is being corrupted?

John

---

### Post by ajgreeny on 2009-12-04
Perhaps the xfix from a small menu in recovery mode no longer exists.  However, I am not sure I can answer your question about the volume problem.

Sorry!

Perhaps the easiest way to go now is to add your new user to the admin group and all other groups that your original user was a member of, then remove the old user and chown the files in the original users home to your new user.  At least that way you should overcome the login problem.

Alternatively, just rename all the config folders in your old home that may be causing the problem and try again.  Add **bak** to the folder names of .gconf, .config, .gnome and .gnome2, and see if that helps as a new user did.  Then one by one you can restore the original folders to see which was at fault, if any of them.

---

### Post by JohnMoriarty on 2009-12-05
Thanks ajgreeny.

I tried renaming the config folders as sugggested, and this solved the problem. I narrowed the problem down to the .config folder and restored the others and have restored most of the the contents of .config (e.g. autostart and stuff relating to particular applications) and I now have everything up and running again and I've tested a few times through reboot and logout/in. Everything seems fine, so thank you very much.

(A lot of icons seem to have changed design, but I quite like the result and so this is a happy side effect.)

I presume the problem was caused by a file in .config being corrupted, which would be fixed by fsck, and consequently explain the loss of the setting for the volume. Perhaps the problem lies with whichever file the volume is recorded in.

John

---

### Post by ajgreeny on 2009-12-05
I'm very glad I could help.  It is very seldom that your sort of problem can not be solved without a reinstall.  At worst it is renaming of all hidden folders in your home and restoring one by one until it all goes bottom up again.

That is one of the great joys of linux, you have an OS still with a GUI attached on top, unlike windows where everything is so tightly integrated you can very often not do anything at all.

---

