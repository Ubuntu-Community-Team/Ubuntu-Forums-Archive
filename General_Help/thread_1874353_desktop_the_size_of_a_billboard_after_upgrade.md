---
title: "desktop the size of a billboard after upgrade"
date: 2011-11-02
forum: General Help
---

### Post by RD2112 on 2011-11-02
hi all, after a few days of ignoring the update i decided to upgrade, upon the finish of the installation of ugrade my desktop is huge, i can see just part of the right side of loggin box, agter loggin i can no longer see the top bar that was there before i put my pasword in the box, i tried ctrl alt F1 and F5 to open a terminal. but can;t see anything there. if i type a few words i can start to see things again. until it goes to next line.

i decided to try to go in via live cd, and move some files around incase i need to reinstall, but while i am in live cd, is there a config file i can modify so i can resize my desktop, or am i seeinga possible video card issue? 

any help would be great.

thanks,.

---

### Post by notgary on 2011-11-10
Before you go ahead and reinstall, you could try summoning the Dash using the <Super> key, otherwise known as the Windows key. From there you can type "Display" into the search box and the first thing that should appear in the list of results are the display settings. From here, you can check what your display resolution is like.

You can also use the Spaces feature to move windows around your desktop. You can run it either by clicking on the icon in the Launcher or following the same process for opening it from the Dash as you did for the display settings. When your desktop zooms out and show you the four different spaces, you can click and drag applications between the different spaces, and you can use this to position your display settings window in such a way that it isn't running off the side of the screen.

---

### Post by proxx1850 on 2011-11-10
Could you give us some more details?
What card are you using ?

Maybe you could drop into a tty and backup your xorg.conf file,then delete the original one and reboot.
You will probably end up in safe mode, and reconfigure from there on.

---

