---
title: "Need to fix Ubuntu after upgrade"
date: 2010-10-10
forum: General Help
---

### Post by Quadunit404 on 2010-10-10
I managed to get Ubuntu to boot again and I have the NVIDIA-supplied GeForce 9100M G drivers installed (downloaded from their site) but I still have some things left to do.

- The desktop wallpaper is not visible; it's covered up by a buncha white.
- I cannot open executable files. It says that there is no application installed for executables (I wish I was making that up)
- If I right click on the desktop I can't do anything on it; the cursor is replaced with the busy cursor.
- If I try to open an application it says "Maximum number of clients reached" and "cannot open screen :0.0"

Should I try backing up my settings and stuff like that and reinstalling Ubuntu?

---

### Post by frogotronic on 2010-10-10
executables...*.exe files?

- CH

---

### Post by 1ceblu3 on 2010-10-10
Well for one thing you can't really install .exe files in ubuntu..  			 		   		 		 		You can try WINE, but honestly, the best thing to do is to check for a Linux alternative.

---

### Post by Quadunit404 on 2010-10-10
By executables, I meant Linux executables ;)

And not even Wine works; that's how bad my situation is.

---

### Post by xjesse on 2010-10-10
He asked if he should back up and reinstall instead everyone above jumps on him for saying executable files. 

"In computing, an executable (file) causes a computer "to perform indicated tasks according to encoded instructions," as opposed to a file that only contains data. ..."

[en.wikipedia.org/wiki/Executable_program]("en.wikipedia.org/wiki/Executable_program")

Anyways, reboot Ubuntu info Failsafex by tapping left shift at boot up. Let us know if the problem is still there.

Also, did you have any ppas in your repository before the upgrade? Maybe xorg edgers? These need to be purged before distr-upgrades.

---

### Post by Quadunit404 on 2010-10-10
I ultimately reinstalled Ubuntu as it was broken beyond belief. Now I'm working on restoring the backup of my /home folder I made and reinstalling my crap.

---

