---
title: "keyboard shortcuts"
date: 2012-04-29
forum: General Help
---

### Post by tomatoe on 2012-04-29
Hello,

I was was wondering, is there a way to make keyboard shortcuts? For example ctrl+alt+f opens firefox.

Regards.

---

### Post by tomatoe on 2012-04-29
Found it!

**Text Entry Shortcuts**

 If  you want to have quick access to lines of text by using a hotkey, for  example to enter your email address in forms, then you can use  xbindkeys. Xbindkeys has a GUI utility to allow easy settings of  hotkeys, but be aware that it's a little more complicated than the  default Ubuntu Shortcutkeys interface. 
Install xbindkeys   
sudo apt-get install xbindkeysCreate the default config file for xbindkeys 
xbindkeys --defaults > /home/your-user-name/.xbindkeysrcWhen thats done, install xbindkeys-config, the GUI for xbindkeys 
sudo apt-get install xbindkeys-configNow the utility the actually does the "typing" 
sudo apt-get install xvkbdOnce each is installed, start both applications by bringing up "Run Application" with ALT -F2. 
xbindkeysand
xbindkeys-config 
To  keep the xbindkeys hotkeys active when you next start the computer you  will have to add a new session, System --> Preferences -->  Sessions. Put in the command "xbindkeys" into the command field (without  the quotes). 


[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

---

