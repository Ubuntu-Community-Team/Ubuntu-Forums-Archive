---
title: "firefox after update"
date: 2011-10-09
forum: General Help
---

### Post by ronbrooks on 2011-10-09
I am using Ubuntu 11.04 64 bit and the update manager updated firefox and now I am having trouble with it.  When I shut down firefox I get an error message the the web page is not responding.  If I wait a little bit it will close but then when I try to start it again it will start in the page I just left and not my home page.  Sometimes it will not start at all and I will have to restart the computer to get it to open again. I have tried to reinstall it but that didn't work.

Is anyone else having this trouble and dose anyone know how to fix it.

---

### Post by Frogs Hair on 2011-10-09
Check your home page preferences in Preferences > General  . There is an option to start from the last session , but you would have had to set Firefox to do that .  This does not explain why Firefox won't  start some times . You could also try to start Firefox from the terminal and see if any errors are displayed .

---

### Post by ajgreeny on 2011-10-09
Run firefox with the command ```
firefox -no-remote -P
``` to start the profile manager and make a new profile to see if that helps.  Alternatively temporarily rename your current **/home/user/.mozila/firefox/*alphanum*.default** as a backup and start firefox.
See [http://ubuntuforums.org/showthread.php?p=10467399](http://ubuntuforums.org/showthread.php?p=10467399) for all the details of what the profile manager can do, but don't delete the old profile as you may need to copy back all your bookmarks.

Runing a new profile will tell you if it is the old profile that is causing the problem or some inherent problem in the installation of firefox itself.

---

### Post by ronbrooks on 2011-10-09
> **ajgreeny said:**
> Run firefox with the command ```
firefox -no-remote -P
``` to start the profile manager and make a new profile to see if that helps.  Alternatively temporarily rename your current **/home/user/.mozila/firefox/*alphanum*.default** as a backup and start firefox.
See [http://ubuntuforums.org/showthread.php?p=10467399](http://ubuntuforums.org/showthread.php?p=10467399) for all the details of what the profile manager can do, but don't delete the old profile as you may need to copy back all your bookmarks.

Runing a new profile will tell you if it is the old profile that is causing the problem or some inherent problem in the installation of firefox itself.

(firefox:1736): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

is what I get when I run firefox from the script that you said to use. Could this be the trouble as to why it is not shutting down right. 

It runs fine while it it up and running it is just when I close firefox that the trouble started.

---

### Post by ajgreeny on 2011-10-09
So can I assume you don't see the dialog as in my screenshot from the ```
firefox -no-remote -P
``` command?

---

### Post by ronbrooks on 2011-10-09
Thank You ajgreeny for your help. Yes I got that page OK and I changed the profile and that fixed it.  I did have to add my book marks and also had to add my address book and calendar in Thunderbird.  That was not a problem as I just got them off my other computer.  I still don't know why the default setting didn't work.  I think it has something to do with ad block program.  I tried to reinstall it but it wouldn't install.

---

