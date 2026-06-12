---
title: "I have made a STUPID mistake... :\"
date: 2011-05-02
forum: General Help
---

### Post by BoPe86 on 2011-05-02
My x64 Ubuntu is about 1.5 years old. After every upgrade it just run slower and slower. I did some digging and found that file system (JFS) got fragmented so i made a little experiment - i cut /usr/share/icons/ folder and pasted it to my /home partition (/ partition is 30Gb, /home partition is 126 gb). After that, i moved "icons" folder back to /usr/share and restarted my computer. Icons really loaded faster then before! That's why i decided to use my old "karmic" live cd and cut whole "/" partition to backup drive, then move it back. I believed that then my system would work faster.

So, i did it! Moving (almost) everything from "/" partition to backup drive worked nice, but there was a red flag - "properties" window showed that after moving to new location, files on new location had few megabytes LESS then before moving! File number was ok (all files moved) and after some googling i found out that it's some Nautilus bug (showing wrong folder size). I continued and moved files back from backup drive (also Linux, JFS, drive) to my "/" partition and tryed to boot my sistem. Any now, here we go:

First, before login dialog is shown i got some nasty messages: 

"Could not update ICEauthority file /var/lib/gdm/.ICEauthority". 

After that message there's another "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

After that second message, i'm logged in but only wallpaper is shown (NOT the one i use) and mouse keeps "busy" state. HDD is idle. Recovery mode is ok, i can login i even reinstalled "gdm" (hoping that it could solve my problem) but no luck!

What should i do? Please, help me. I can't believe that Nautilus (the one no "Karmic" live cd) is unable to CUT files properly from one (JFS) disk to another (JFS disk) without problems?!

---

### Post by kalyp on 2011-05-02
I'm having that exact same problem right now and from what I'm seeing on the forum so far it's a permission problem. In my case, I did a clean install (user 1000) while I'm user 929 in my home folder. For .ICEauthority, giving rw permissions to everyone solved the problem. 
For the 2nd message look at [http://ubuntuforums.org/showthread.php?t=917306](http://ubuntuforums.org/showthread.php?t=917306)

---

### Post by BoPe86 on 2011-05-02
Well, i solved almost everything, got my system back up. It was strange, no "shut down" option in menu, when i click "restart" or "shut down" at login dialog computer just hangs but...it was something. I managed to solve problems with "sanity check" by setting user permissions to /home/user folder, and by setting root permissions to /var/lib/gdm folder (somehow, owner of that folder was "gdm", not "root").

BUT THEN!

I look up my old linux (another computer) and decided that all folders at "/" (of course, except "/home") probably should be owned by root with "read only" FILE access to all other groups. I have applied "owner root, all others read-only" access to ALL files in "/" and that's beginning of another nightmare - now when i try to boot my linux i only got "alloc magic broken at 0xfafa (some address). Press Enter to exit" message!

How to solve this new problem? :D

P.S. I'm just trying to be productive by solving problems myself but it turns out that i create even bigger problems... I have no idea how i got to "hey, let's make all root files read-only"... :\

---

