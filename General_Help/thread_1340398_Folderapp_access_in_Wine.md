---
title: "Folder/app access in Wine"
date: 2009-11-28
forum: General Help
---

### Post by johnhdsi on 2009-11-28
Hi all, I am having an issue in Wine where I installed WoW and now the folder permissions keep getting taken away from me. I had another thread that asked about it but the only answer I got was "do a full Ubuntu, Wine and WoW re-install" . Everything is working fine on my system, I have installed Steam through Wine and I had no issues there but for whatever reason I keep getting the same error 

Failed to change to directory '/home/john/.wine/dosdevices/c:/Program Files/World of Warcraft/' (Permission denied)

When I check my permissions through the CLI I get 
d---rwx--- 5 john john 4096 2009-11-28 12:52 World of Warcraft

However I can manually change the permission and it sticks for a few minutes then goes back to restricted. I'm not into the whole "Dump your system and start over" I want to try and fix this and make sure if it was something I did that I don't do it again and if I do run into the same problem down the road I want to be able to take care of it not keep reloading Ubuntu. Any ideas are much appreciated. I'm running 9.04 with Wine ver. 1.1.32

Thanks in advance!!

John

---

### Post by ed-koala on 2009-11-28
This is due to a change made to WoW's  launcher in the latest patch.

The only solution I know of, at least for now, is to manually go into your .wine folder, find the world of warcraft folder (under drive_c is mine) and change the permissions.

You ****MUST**** run WoW using the wow.exe executable. If you use the launcher.exe, it will change the permissions again and fail to run.

I'm sure a solution will be forthcoming from Wine soon ... or WoW, or someone.  :)

---

### Post by jmcgovern on 2009-11-28
The issue is some sort of bug with the 'launcher.exe' program.   It changes the folder permissions upon running.  The only workaround I've discovered at this point is to not run the 'launcher.exe'.  instead, run 'wow.exe' directly, and the game will start fine.  The bug is something in how the launcher,exe works with Wine, so it's not likely to be fixed as wine is not officially supported.

---

### Post by johnhdsi on 2009-11-28
Cool...Thank you very much I'll give it a shot and see how it works.

---

