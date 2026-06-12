---
title: "A number of odd problems lately..."
date: 2011-03-08
forum: General Help
---

### Post by indigoshift on 2011-03-08
Using 10.04.1 LTS version, on an old Dell Latitude D610.  No complaints, but a couple very weird bugs popping up.  Such as:

1.  My thumb drives aren't recognized anymore.  I used to just plug them into the USB port (any USB port) and within ten seconds, a window would pop up for them.  Nothing happens now, and I haven't figured out the proper way to mount them from the command line.  Truth be told, I'd like the auto-detect to start working again.  I transfer files between this laptop and my XP desktop quite often.

2.  Trash can is gone.  The icon is gone from the bottom panel and when I try to navigate to it normally, it throws an error that says:

> Sorry, could not display all the contents of "trash": Operation not supported.

I'd like to get in there and empty it at some point, but can't.  Would like that panel icon back, really.

3.  Opening a terminal takes a while.  The window opens right away, but it takes five or six seconds for the prompt to appear.  It's never done that before.  I don't know if that's indicative of a larger problem.  I don't have more than ten or so aliases, and they've never caused any slowdowns before.

So there you go!  If any of these problems can be fixed, please let me know. And thanks in advance!

---

### Post by dirty_harry on 2011-03-08
I hope to answer a bit of your questions:


[LIST=1]
[*]for mounting manually look here  [https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting](https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting) ; maybe  you turned of automount in nautilus?
[*]add your trashfolder-icon to the panel by right-clicking on it and you can browser your trash folder on the command line: 
    ```
cd ~/.local/share/Trash/files/
``` to empty your trash-folder completely:```
rm -rf ~/.local/share/Trash/files/*
```
[*]don't know; see top or system-monitor for what services are running; any information in the logs after you started terminal?
[/LIST]
 All those issues appeared a once or over a short period of time?

hope it helps

---

### Post by indigoshift on 2011-03-09
In gconf-editor, both media_automount and media_automount_open are checked, but no thumbdrive I plug into any USB port seem to be recognized anymore.  Mounting via command line doesn't seem to work, either.

As for the trash: I've right-clicked the panel to try and add the trash icon, but it doesn't work.  Nothing happens.

Thanks for the path to the trash folder!  I did manage to get it emptied from the command line.

All these issues happened within an update or two of each other, about a month or so ago.  I was busy with real-life nonsense at the time, and am just not finding time to look into these problems.

Thanks again for the help!  This is the first time in five years or so that I've had this much trouble after an update.  It's very odd.

---

### Post by dirty_harry on 2011-03-09
for usb related issues I always use "lsusb" and "dmeg | tail"... but without logs and some more information I will be difficult.

the trash icon thing is quite odd.

I am not sure, but with your Dell Latitude you could post in this Dell Subforum for further help...

---

### Post by indigoshift on 2011-03-19
lsusb is new to me, but I'm not sure what to do with that information.  Not familiar with "dmeg | tail" though.  dmesg, perhaps?

---

### Post by indigoshift on 2011-07-22
Months later, and still no solution.  I've noticed that all my problems with 10.04 are common problems with few answers.  From the thumbdrives no longer being recognized to the "boot with live CD to fsck the harddrive again" every fourth or fifth boot, it seems that the OS I fell in love with back in late 2005 is something I can't rely on anymore.

As a result, I've uninstalled Ubuntu and moved to Mandriva 2010.2.  It's a great OS, although I'm still getting used to KDE after using Gnome for so many years.  :D

Thanks to everyone on the Ubuntu forums for all your help over the years!  I wish you nice people nothing but the best.

Adios! ):P

---

