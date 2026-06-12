---
title: "cannot save changes in startup applications"
date: 2009-12-21
forum: General Help
---

### Post by ruister on 2009-12-21
Hi,

I am running Karmic Koala (Ubuntu 9.10) on an older Gateway m275.  I have gotten most everything running except, that I cannot get changes to "Startup Applications" to stick.  IOW any applications that I add or remove from "Startup Applications" are gone when I restart the system, or even when I restart "Startup Applications".  Any ideas?

Thanks,
-Rui

---

### Post by dearingj on 2009-12-21
Try this: Open a terminal and run "gnome-session-properties". Post any terminal output you see - I bet you'll get something about being unable to save a file.

---

### Post by claracc on 2009-12-21
You can try the following:
System --> preferences --> apps at the beginning, in the window you select options and then thick in the option "automatically remember apps executing when login out".

Regards

---

### Post by johnjust on 2010-01-12
I'm having this same issue, and I get no output from "gnome-session-properties" in a terminal.

I've been trying to add the Conky startup script, but every time I restart my computer to test it out, my changes are gone.

---

### Post by john newbuntu on 2010-01-13
Like 3rdalbum suggests here, perhaps you are in a failsafe mode.  Log out and log back in into regular gnome mode and then see if you are able to set your scripts/jobs.
[http://ubuntuforums.org/showpost.php?p=8506313&postcount=13](http://ubuntuforums.org/showpost.php?p=8506313&postcount=13)

---

### Post by johnjust on 2010-01-13
I am logging into "GNOME", not the "Failsafe GNOME" session.

I tested adding "Terminal" as a startup application, and it actually does save and execute on next reboot.

What I was trying to do was add Conky as a startup application - not by the "conky" command, but by a shell script:

```

#!/bin/bash
sleep 15 && conky;

```

Next, I change permissions to make it executable.

Then, I add that to the "Startup Applications", with either of the following commands:

```
/home/justin/conky_startup.sh
```

```
sh /home/justin/conky_startup.sh
```

And after a reboot, it's no longer listed in "Startup Applications".  Once I thought I might have hit "Cancel" instead of "Add", but I tried this about 5 times, and it still disappears.

---

### Post by vyszard on 2010-01-13
I've got the same problem here. No matter what I do to Startup Applications Preferences, it keeps revert back after I close the window. Badly need help..

---

### Post by john newbuntu on 2010-01-13
The one other thing is to give yourself the permission to administer the system and see if it helps.  system->admin->users/groups->click to make changes. enter password.Choose your id->properties->user previlege->administer the system.
Set up a new startup job and log back in and see if it works.

If that does not work,lets try the brute force/workaround.  Go to /etc/xdg/autostart.
Create a script as a root like:

sudo cp nm-applet.desktop conky.desktop

Modify conky.desktop using gksudo as follows:
Change the Name to conky. Change 'Exec=' to 'Exec=sh -c /home/justin/conky_startup.sh'
Remove the AutostartCondition line.

Make sure the permission on the conky.desktop file is 744 and is owned by root.
Now log on to a new gnome session and cross fingers.

---

### Post by johnjust on 2010-01-13
> **john newbuntu said:**
> The one other thing is to give yourself the permission to administer the system and see if it helps.  system->admin->users/groups->click to make changes. enter password.Choose your id->properties->user previlege->administer the system.
Set up a new startup job and log back in and see if it works.

If that does not work,lets try the brute force/workaround.  Go to /etc/xdg/autostart.
Create a script as a root like:

sudo cp nm-applet.desktop conky.desktop

Modify conky.desktop using gksudo as follows:
Change the Name to conky. Change 'Exec=' to 'Exec=sh -c /home/justin/conky_startup.sh'
Remove the AutostartCondition line.

Make sure the permission on the conky.desktop file is 744 and is owned by root.
Now log on to a new gnome session and cross fingers.

Still no dice, tried everything in there...  The first time I created that shell script, I had a sudo gedit opened, and I thought that might have been my problem - the file was owned by root and not my normal user.  Turns out that didn't make a difference.

I think the thing here isn't so much that it's just this one item that keeps getting removed from the list, but the fact that this behavior started all of a sudden.  I've been using Ubuntu since Feisty, and I've also been manipulating my startup applications for some time now, I've just never had things just disappear like this before.

I've made a couple posts here and there about my Karmic install being perfect, with no problems - but maybe there is a problem or two after all...

Though this is a little annoying, I can live with manually starting conky when I boot up, I'm not one of those helpless people who complain when I have to do a little work.

Thanks for the suggestions, I'll definitely update this post if I find a solution.

---

### Post by john newbuntu on 2010-01-13
One more thing:  Throw your shell script in the directory /etc/X11/Xsession.d with the following permission (if you know what I mean)
-rw-r--r-- 1 root root

---

### Post by vyszard on 2010-01-18
Mine solved. Apparently it was an issue of file permission. I can't write into ~/.config/autostart because the folder owned by root.
So referring to this documentation [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions") I changed the file permission with this command:

```
$ sudo chmod o+wrx -R /home/[user]/.config/autostart
```

Everything work just fine now. :D :D

---

### Post by tonyshangrila on 2010-01-24
> **vyszard said:**
> Mine solved. Apparently it was an issue of file permission. I can't write into ~/.config/autostart because the folder owned by root.
So referring to this documentation [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions") I changed the file permission with this command:

```
$ sudo chmod o+wrx -R /home/[user]/.config/autostart
```

Everything work just fine now. :D :D

Perfect!  Worked for me, too.  Thanks.

---

