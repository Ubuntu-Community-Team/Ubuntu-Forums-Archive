---
title: "My files are simply disappearing before my eyes"
date: 2009-11-05
forum: General Help
---

### Post by Maheriano on 2009-11-05
I just finished a 9.1 upgrade and as soon as I rebooted I tried copying files off a flash drive onto a folder on my desktop. I held SHIFT so that they would disappear from the flash drive as they were copied to the Desktop. It was 8 gigs worth of movies and shows so it took a while and when there was a minute or so left, the transfer window disappeared.

I thought that was weird but figured maybe I wasn't paying attention and time went by faster than I thought. I right clicked the flash drive icon and clicked Safely Remove so I could take it out. That finished, I removed the flash drive and loaded it up with more stuff from my laptop. While that was copying, I took the files that I just copied to the desktop and started dropping them in their respective MOVIES/SHOWS folders so they can be picked up by Moovida. After they finished copying a bunch of my movie files were gone but the folders were still there. Weird. So I exited the folder and dragged another movie to the folder. As soon as I did that, the MOVIES folder itself disappeared.....WTF? Now it's gone, I can't even see it in Terminal when I CD to the location. Everything is gone, how did that happen? It's not user error neither, been using computers for 15 years. And I'm not drunk.

---

### Post by wilee-nilee on 2009-11-05
I'm not sure what happened here, but any file transfer I do I keep the original and check the data size and the transfer itself for any mistakes. Your computer will delete the thumb in about 2 seconds so having it remove them and transfer at the same time is not a good idea, I hope you find the stuff though. On a Linux system when you do a data size check through properties you get a fairly accurate #. When you darg and drop data files it saves the original as you know but a copy and paste is another good way.

---

### Post by dharmagio on 2009-11-06
I had the same problem but it was different. i was copying audio files between 2 folders and what happened was that my desktop dissapeard, i still dont see the desktop files, but if you go to your /home/"username"/Desktop the files are there for sure, at least my desktop files are.

this ubuntu 9.10 have some serious bugs
i hope they solve this soon

and by the way, anyone knows what's going on with this desktop issue?

---

### Post by Maheriano on 2009-11-06
The files aren't there, not even when I navigate to the directory under Terminal. I even made a new folder called Movies, which should have errored if the other one still existed, and copied more movies into it. Then it disappeared again! Is there some sort of DRM conflict with 9.1? It removes anything labeled as movies?

---

### Post by HiImTye on 2009-11-06
are you using 32bit ubuntu?
were any of them over 4GB?

---

### Post by HiImTye on 2009-11-06
> **dharmagio said:**
> I had the same problem but it was different. i was copying audio files between 2 folders and what happened was that my desktop dissapeard, i still dont see the desktop files, but if you go to your /home/"username"/Desktop the files are there for sure, at least my desktop files are.

this ubuntu 9.10 have some serious bugs
i hope they solve this soon

and by the way, anyone knows what's going on with this desktop issue?
I would do this:

[LIST=1]
[*]system tools>configuration editor
[*]navigate (on the left side) to 'apps/nautilus/preferences'
[*]find (on the right side) 'show desktop'
[*]check it (on the 'value' column)
[/LIST]

---

### Post by dharmagio on 2009-11-06
1. system tools>configuration editor
   2. navigate (on the left side) to 'apps/nautilus/preferences'
   3. find (on the right side) 'show desktop'
   4. check it (on the 'value' column)


sorry but where is that?

i have system/preferences or administration/and cant find any configuration editor?

---

### Post by Maheriano on 2009-11-06
> **HiImTye said:**
> are you using 32bit ubuntu?
were any of them over 4GB?

64 bit, all are about 1.5 gigs per movie. Some may have been close to 4 gigs but only 1 or 2.

---

### Post by HiImTye on 2009-11-06
> **dharmagio said:**
> 1. system tools>configuration editor
   2. navigate (on the left side) to 'apps/nautilus/preferences'
   3. find (on the right side) 'show desktop'
   4. check it (on the 'value' column)


sorry but where is that?

i have system/preferences or administration/and cant find any configuration editor?

system tools is below sound and video. if it isn't there right click on your menu and choose 'edit menu' then navigate to system tools and put a check mark beside configuration editor

> **Maheriano said:**
> 64 bit, all are about 1.5 gigs per movie. Some may have been close to 4 gigs but only 1 or 2.
just checking, 32 bit has a file size limit of 4gb. this would cause problems with files and/or folders

---

### Post by dharmagio on 2009-11-06
thanks i found it
but that box is allready checked

i cant change background picture of the desktop too
and i can copy files from /home/"user"/Desktop
to the visible desktop
but when i restart
they disappear

i use an external monitor in my laptop
maybe that makes it to go wrong
and when i try to save with nvidea 
x server settings, it says 
error failed to parse nvidea 
x server settings to xorg

so everytime i shut-down or restart
i have to set the external monitor
because it cant save to xorg file the 
needed changes.

---

### Post by Maheriano on 2009-11-06
> **dharmagio said:**
> thanks i found it
but that box is allready checked

i cant change background picture of the desktop too
and i can copy files from /home/"user"/Desktop
to the visible desktop
but when i restart
they disappear

i use an external monitor in my laptop
maybe that makes it to go wrong
and when i try to save with nvidea 
x server settings, it says 
error failed to parse nvidea 
x server settings to xorg

so everytime i shut-down or restart
i have to set the external monitor
because it cant save to xorg file the 
needed changes.

This is a permissions issue. It's trying to save the configuration file outside your home directory where only root has write access. If you move the file or grant permissions to your user, you'll be able to write to it. Or what's easier is to just open up the file in gedit ```
sudo gedit <file location>
``` and put your settings in there manually.

---

### Post by P4man on 2009-11-06
simplere yet, run

```
gksudo nvidia-settings
```

then you will be able to save the modified xorg from nvidia applet.
Make sure you deselect the "merge" option unless you know you need it.

---

### Post by alphaniner on 2009-11-06
> **dharmagio said:**
> when i try to save with nvidea 
x server settings, it says 
error failed to parse nvidea 
x server settings to xorg.

If you are launching the nVidia tool from the panel (System -> Administration -> nVidia X Server Settings) you're not being allowed to save because it's not being run as root.  You can simply launch the tool from the terminal with **gksudo /usr/bin/nvidia-settings**, or you can edit the entry in the menu.

To edit the entry, right-click on 'System' on the panel and select 'Edit Menus'.  On the window that appears, select 'Administration' on the right and 'nVidia X Server Settings' on the left.  Then click the 'Properties' button.  In the command field, change **/usr/bin/nvidia-settings** to **gksudo /usr/bin/nvidia-settings**.  Then close the dialog box and the window.  From now on when you launch nVidia Settings from the menu, you will be prompted for your password and will be able to save the changes you make there.

---

### Post by dharmagio on 2009-11-06
all these options are valid
but i still cant save to xorg

the following message appears:

Failed to parse existing X config file '/etc/X11/xorg.conf'!

and in the terminal gives the following message, and nvidea window close:

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

in last ubuntu version i cood edit xorg manually because the window stays open 
and gives the scrip to be open so i can edit the xorg file with it, but
now just closes the windows when i try to save.

i run it with sudo then with gksudo and even as su, and gives me allways the same message, i never had this problem in other ubuntu versions, only this karmic as a karmic bug!

---

### Post by P4man on 2009-11-06
I guess it means nvidia-settings doesnt understand your current xorg.conf, Possibly its incorrectly formatted. Are you sure you unchecked the "merge" option?

Do you have any settings in xorg.conf that you need?

Either way, id rename your current xorg.conf to xorg.back or something and try again. If you need any settings from the old one, just copy/paste them in after nvidia-settings created a fresh one.

---

### Post by dharmagio on 2009-11-09
i dont know where is that merge option?

well i solved it like this

i made a safe copy of xorg.conf

then i erased the original

so when nvidea trys to save it and dont find xorg it asks to point a path and already show the option to view the code, so now i can copy the code and save it in xorg.conf

because when the file is present, even if its empty allways appear the same error message

---

### Post by Maheriano on 2009-11-09
Can we address my original problem please?

---

