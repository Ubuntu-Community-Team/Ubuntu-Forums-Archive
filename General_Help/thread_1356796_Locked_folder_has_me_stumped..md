---
title: "Locked folder has me stumped."
date: 2009-12-16
forum: General Help
---

### Post by Azerothsbest on 2009-12-16
I was messing around with Wine trying to get my World of Warcraft to function. (whole other problem hardware compatibility issues I think) Now my World of Warcraft folder has a Locked Lock and an X directly under that. I was following on a other forum they said open Terminal and give this command. sudo chown -R username:username folder-name. so It looks like this below.

Name@Name-laptop:~/Desktop$ sudo chown -R Name:Name World of Warcraft

I then get this message in the Terminal. 

chown: cannot access `World': No such file or directory
chown: cannot access `of': No such file or directory
chown: cannot access `Warcraft': No such file or directory

Any ideas? Or was I given false information? Please help thanks :-)

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
the terminal doesn't recognize spaces in filenames. You'll need to use the ls command to see how it's named in the terminal.

---

### Post by SuperSonic4 on 2009-12-16
> **ST3ALTHPSYCH0 said:**
> the terminal doesn't recognize spaces in filenames. You'll need to use the ls command to see how it's named in the terminal.

Or be lazy and use tab completion or quotation marks

" " is shown by "\ " in terminal (without the "")

---

### Post by whiteychs on 2009-12-16
I also play WoW on linux and the problem I think you're having is caused by the WoW Launcher.

A simple:

> sudo chmod 777 World\ of\ Warcraft

fixes it for me

=======
Edit:
I see that you're trying to do this from the desktop!
First, you need to navigate to the .wine/drive_c/Program\ Files/  directory (or wherever your WoW folder is).

---

### Post by Azerothsbest on 2009-12-16
I just got around the problem by Right clicking on the folder and going to Properties --> Permissions, and turned Folder access to Create and delete files. :-D Thanks for all the input!!! I hope I get wow running I'm using a Radeon X600 mobile and my graphics are a bit messed up in the game, like mini-map blocked out and spells not all shown oh + all my fonts are missing xD... But it gives me something to tinker with until I get my desktop parts in. Thanks again for all the speedy replies <3 U all rock :guitar:

---

### Post by eriktheblu on 2009-12-16
I've taken to starting WoW from a panel launcher linked to a script (script file located outside the WoW folder). The script issues the chmod before calling wow.exe (and a second wow.exe, and keyclone). I'll try to remember to post it when I get home.

I never really understood the practice of naming directories in a manner that the CLI cannot interpret. I mean, for those not familiar with the CLI sure, but Blizzard (and MS) should know better than to include spaces in their default directories.

It's perfectly safe to rename your "World of Warcraft" folder to something else to avoid further setbacks.

---

### Post by whiteychs on 2009-12-16
> **eriktheblu said:**
> 
I never really understood the practice of naming directories in a manner that the CLI cannot interpret. I mean, for those not familiar with the CLI sure, but Blizzard (and MS) should know better than to include spaces in their default directories.


Even when I'm on a Windows box, I still adhere to using underscores instead of spaces. I share your confusion.  :confused:

---

### Post by doas777 on 2009-12-16
spaces in filenames are a pox upon this land, when passing ruffians may say 'NEEEEEH!' to old ladies at will. I am a shrubber by trade; Roger the Shrubber.

I heard a few weeks ago that a wow update had started changing file permissions on each load. not sure if this is related.

---

### Post by whiteychs on 2009-12-16
> **doas777 said:**
> 
I heard a few weeks ago that a wow update had started changing file permissions on each load. not sure if this is related.

It's just the launcher. You only have to chmod the folder after an update which always calls the launcher.  If you run directly from Wow.exe, it shouldn't change the permissions.

---

