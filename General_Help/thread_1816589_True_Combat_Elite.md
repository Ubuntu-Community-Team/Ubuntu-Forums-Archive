---
title: "True Combat Elite"
date: 2011-08-02
forum: General Help
---

### Post by nankura on 2011-08-02
Hey guys

ok basically. i installed enemy territory using .runs and downloads and things went weird. had troubles, finally got it installed and patched

Then i installed TCE, and i had a gui install no like on youtube with the console so i think i made a mistake, and now TCE is installed into some //tc-elite folder which i cant locate or find and the exe on the desktop wont start up

So i removed enemy territory completely which went fine, but didnt remove TCE. ive tried rm commands etc. 

So i finally thought it was gone. 

So i downloaded enemy territory from playdeb since its all done for you and prepatched and works great. the install went great. thats all fine, ET is fine

so i go to install TCE with the .run installer, and it says that enemy territory isnt installed. so i attempted to move the installer to the actual Enemy territory folder. the game directory, and ran the .run from there to see if it made a difference

and now it says that TCE is already installed, please uninstall

i found some traces of the true combat files in the main filesystem and managed to forcefully remove //tc-elite, so now its saying that i dont have enemy territory installed. when the playdeb package is the latest version of ET and installed just fine and the game runs


edit: it also says this message every now and then , the error  changes each time i run the .run installer and now it says that TCE is  already installed, please uninstall

so im abit stuck

---

### Post by nankura on 2011-08-02
ok after reading alot of guides, trying alot of solutions. i ended up with this after extracting the .run contents into a folder tce and editing the search.sh which contains the install path to direct to the installation folder

Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /usr/share/games/enemy-territory
Installing in /usr/share/games/enemy-territory/
Seems like Return to Castle Wolfenstein: Enemy Territory was installed by another user.
You have to install True Combat: Elite as the same user who did install Return to Castle Wolfenstein: Enemy Territory.

---

### Post by nankura on 2011-08-03
ok solution solved myself. thanks for the... help?

Anyway, i solved this via removing everything ET, and mods, and doing a chown on the usr folder in the root directory

Installed ET and TCE without a problem after doing a chown and everything runs fine

---

