---
title: "lost panel"
date: 2010-10-30
forum: General Help
---

### Post by houndhen on 2010-10-30
No menu, can't find a keyboard combination to start terminal. Ubuntu 10.10 32 bit. Do I have to re-install?

---

### Post by yabbadabbadont on 2010-10-30
Try using Alt-F2.  If it opens a "Run Application" dialog, then you can run gnome-panel.

---

### Post by houndhen on 2010-10-30
> **yabbadabbadont said:**
> Try using Alt-F2.  If it opens a "Run Application" dialog, then you can run gnome-panel.Tried ALt-F2 and every other key combo I could think of. And when I get dumped out of the gui I don't know how to get back into the gui except to reboot.

All I have showing on the desktop is the background picture. Can't figure out how to get the run menu to come up. I restored the panel once before by getting the run window to come up and searching for gnome-terminal. I've got the fix but can't get to terminal. 

I added some application launchers to the panel next to the one for firefox and then when I rebooted there was no panel.

---

### Post by yabbadabbadont on 2010-10-30
If you can get to the text console by hitting Ctrl-Alt-F1, login and try copying /usr/share/applications/gnome-panel.desktop to the ~/.config/autostart directory.  Then you could run "sudo service gdm restart" to restart Xorg and hopefully take you back to the graphical login screen.

Edit: This probably won't work, now that I think about it some more.  You probably need to clear your gnome-panel configuration by moving (or removing) the ~/.gconf/apps/panel directory.  Which you can do after you login at the text console.

---

### Post by houndhen on 2010-10-30
> **yabbadabbadont said:**
> Edit: This probably won't work, now that I think about it some more.  You probably need to clear your gnome-panel configuration by moving (or removing) the ~/.gconf/apps/panel directory.  Which you can do after you login at the text console.I have managed to remove the panel directory in ~/.gconf/apps/. The thing that I did once before was from the forum and it said to open a terminal and run "gconftool-2 --shutdown, rm -rf ~/.gconf/apps/panel, pkill gnome-panel". It worked before but now I can't get to a terminal from inside ubuntu. I got out of the gui and logged in at the text console and ran the above again. I rebooted and there was still no panel or menu nor could I get a terminal or anything else to open. I have used the installation disk and got into the partition where ubuntu is installed and checked and there is no panel directory at ~/.gconf/apps/. Any more ideas? 

I may just have to re-install. I had rather not but will if there is no way to get the panel back. Someone should be guru enough to know how but I know it is not me. The keyboard shortcuts aren't working. Maybe that might be part of the problem. 

Why is the panel so touchy; or maybe I should say unstable?


after edit
I have re-installed and remember prior to the lost panel that I completely removed all files that had evolution in them. That most likely caused the whole thing. Ya live and learn....

---

