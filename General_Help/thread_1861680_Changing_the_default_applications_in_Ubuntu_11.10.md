---
title: "Changing the default applications in Ubuntu 11.10"
date: 2011-10-15
forum: General Help
---

### Post by Meelad on 2011-10-15
I tried changing the default application to play my music and video files through: System Settings => System Info => Default Applications, but the system ignores my newly set applications and my music and video files keep opening with Movie Player and Banshee by default.. Logging out and in again didn't help either..

Any ideas why??

---

### Post by Buttink on 2011-10-18
I have this same problem, and the only thing I can think of is that Ubuntu's default apps are different from Gnome's default apps. But honestly, I have no idea. :(

---

### Post by mc4man on 2011-10-18
When you change the default for music player and or video player what is done is a line(s) in ~/.local/share/applications/mimeapps.list is created or edited.
Thats it.

For audio this line in the [Default Applications] section will receive the .desktop of whatever app you've chosen
audio/x-vorbis+ogg=

For video this line
video/x-ogm+ogg=

Those lines can be used elsewhere  - for example the 'Listen to Music' icon in the dash uses what is shown on the audio/x-vorbis+ogg= line

The changing of defaults for individual filetypes  should be done individually which will also write the changes to ~/.local/share/applications/mimeapps.list
 
The idea to have users do a bulk rewrite of /ect/gnome/defaults.list is ill-advised & quite the overkill. I would never recommend that.

It's not really a big deal - only takes most users a min or so to set new defaults on a per .whatever for the ones they use

---

### Post by scottbomb on 2011-10-18
Not sure if this works in gnome or kde, but in Xubuntu, right-click any file of the type you want to change. Choose properties. Change selection in "open with" drop-down menu. All files of that type will now open with the program you chose.

---

### Post by Meelad on 2011-10-18
Thanks guys! I actually found a solution and I put down an easy command to achieve that in this thread..

[http://ubuntuforums.org/showthread.php?t=1863257](http://ubuntuforums.org/showthread.php?t=1863257)

And scottbomb, you're right, but I was looking for some way to change the default app for ALL the file types currently associated with a specific app, for example if I want to open ALL music file types with Audacious instead of Banshee by default (through double clicking).

---

