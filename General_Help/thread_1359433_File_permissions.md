---
title: "File permissions"
date: 2009-12-19
forum: General Help
---

### Post by charlton2142 on 2009-12-19
Hey guys I need some help with file permissions. I currently have WoW fully installed and its running alright but everytime I want to start it up i have to change the file permissions by navigating to: .wine/drive_c then I have to run "sudo chmod a+rwx World\ of\ Warcraft"

After the game is exited the permissions on the folder revert to locked. if anyone could help me change this it would be appreciated 

thanks

---

### Post by ajgreeny on 2009-12-19
I don't think you should have used **sudo** for the command as that will mean that the permissions are changed for root, but not perhaps for the user, ie, yourself.

All the user's home files/folders in ~/.wine should belong to your user, so check that they are yours first in nautilus (right click and choose Properties->Permissions tab).  You should be able to make them all read/write/execute from the permissions tab without using sudo.

---

### Post by charlton2142 on 2009-12-20
I tried this. This has allowed me to run the game by navigating to the WoW.exe. Im not able to run it from a launcher. And it reverts back to locked after I exit he game. Additionally im not sure if this is connected to the same issue but everytime I start the game I loose all my settings. I have to skip through the video and re-accept the EULA and TOS

thanks for helping

---

### Post by charlton2142 on 2009-12-20
Alright so I fixed the settings issue by replacing the Config.WTF file but im still having problems with the folder Locking up all the time

---

### Post by fhslacrosse13 on 2010-01-13
I too, am having the permissions error.  Only I have no luck with getting the game to work.  The launcher will come up, but after I hit play it seems to crash and change my file permissions.

---

### Post by savaan on 2010-04-25
I'm having the same issue on Ubuntu Karmic. I FINALLY got the permissions to stay on the folder (my launcher still won't work) and I'm able to navigate to the WoW.exe file. I can click on it, but then my graphics on my desktop all go to 800x600 and .... nothing. I have to log out and log back in to get my graphics back to normal

---

### Post by alinamegas on 2010-04-25
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]I have removed permissions to open files. Now i need everone on network to open files but all it has given access to is the main folder not subfolders and files how do i allow them to view all files etc in this folder?

[/FONT][/COLOR][/FONT][/COLOR]

---

