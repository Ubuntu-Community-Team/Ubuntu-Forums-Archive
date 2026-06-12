---
title: "LibreOffice Suddenly Crashing on Splash"
date: 2012-05-31
forum: General Help
---

### Post by toseethefruit on 2012-05-31
Hello everyone,

I've got a problem that I've been unable to figure out. I would be very grateful for any help that you would be able to offer me. 

I'm running Ubuntu 12.04 on a Dell Inspiron E1505 using LXDE. I have LibreOffice 3.5.3 installed from the Ubuntu Software Center. As of yesterday, LibreOffice (specifically, Writer and Calc) were working fine. Today, though, I booted into Ubuntu and found that none of the LibreOffice programs will run. They all load the splash screen, but the progress bar doesn't move, CPU usage jumps to 100% for approximately 10 seconds, and then the splash screen closes (and the program does not open). I've tried running Writer in terminal using lowriter, but with no effect: the splash screen again crashes, and no error message is shown in the terminal. 

As I remember, I did not perform any system updates yesterday. I've tried completely uninstalling and re-installing LibreOffice on my computer, and have confirmed that LibreOffice does not work in Unity 2D, either.

Might anyone have any suggestions about how to begin figuring out what the problem is here?

Thanks very much!

-J.

---

### Post by ajgreeny on 2012-05-31
A corrupted configuration is most likely the cause.

See if renaming the folder **/home/user/.config/libreoffice** as a backup stops the crash happening.  If it does, you can try dragging the subfolders from the old renamed version into the new one, one at a time, until the crashes start happening again.

---

### Post by toseethefruit on 2012-05-31
ajgreeny,

Thanks so much! That certainly was a step in the right direction! I had tried renaming /home/.libreoffice, but didn't realize that there was a different folder at the location that you specified. I can now launch Writer and Calc through the terminal using lowriter and localc, respectively.

However, this seems to be the only way that I can launch these programs now -- none of my shortcuts (nor simply double-clicking on files associated with the programs) launches LibreOffice. Might you, or anyone else, have an idea about why that might be?

Again, thank you!

---

### Post by ajgreeny on 2012-05-31
> **toseethefruit said:**
> ajgreeny,

Thanks so much! That certainly was a step in the right direction! I had tried renaming /home/.libreoffice, but didn't realize that there was a different folder at the location that you specified. I can now launch Writer and Calc through the terminal using lowriter and localc, respectively.

However, this seems to be the only way that I can launch these programs now -- none of my shortcuts (nor simply double-clicking on files associated with the programs) launches LibreOffice. Might you, or anyone else, have an idea about why that might be?

Again, thank you!
Try right clicking on a file in the filemanager nautilus and choosing **Properties > Open with** tab and choose LO there.  It may still be set as OOo.

Where are those shortcuts that don't work?  have you put them on the desktop or are you talking about the launchbar on the left of screen? 

You may need to make the shortcuts executable by again using a right click **Properties > Permissions** tab.  If that doesn't work try copying the appropriate .desktop file from /usr/share/applications, again making it executable, and if that still does not work copy the .desktop from /usr/lib/libreoffice/share/xdg and again make it executable.

---

### Post by toseethefruit on 2012-05-31
ajgreeny,

Again, thank you! When I did that, it told me that it couldn't find libreoffice-common. From there, I figured out what needed to be done. In short, after running ```
sudo apt-get remove libreoffice-common
``` and then ```
sudo apt-get install libreoffice-common
```, then reinstalling each of the individual LibreOffice programs through the Software Center, everything is working again.

I appreciate your help; this was really confusing me earlier today.

---

