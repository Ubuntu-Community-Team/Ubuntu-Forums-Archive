---
title: "opengl is breaking??"
date: 2010-04-28
forum: General Help
---

### Post by melissaif on 2010-04-28
I am fairly new to Linux, so please bear with me here. I have a Radeon graphics card and I installed the Radeon driver using this thread: [http://ubuntuforums.org/showthread.php?t=1440323&highlight=RV630](http://ubuntuforums.org/showthread.php?t=1440323&highlight=RV630)

glxgears and glxinfo were both working fine

Then, I compiled a program with the opengl libraries and ran the program. It seg faulted when attempting to load the libraries for visualization.

After this seg fault, I can no longer run glxinfo or glxgears. When I try to run either one of them I get the result:

No protocol specified
Error: unable to open display :0.0

Also, I am running kubuntu 9.10 if this helps.

I am really not sure what is going on here--does anyone have any ideas for troubleshooting this?

---

### Post by Babuloseo on 2010-04-29
> **melissaif said:**
> I am fairly new to Linux, so please bear with me here. I have a Radeon graphics card and I installed the Radeon driver using this thread: [http://ubuntuforums.org/showthread.php?t=1440323&highlight=RV630](http://ubuntuforums.org/showthread.php?t=1440323&highlight=RV630)

glxgears and glxinfo were both working fine

Then, I compiled a program with the opengl libraries and ran the program. It seg faulted when attempting to load the libraries for visualization.

After this seg fault, I can no longer run glxinfo or glxgears. When I try to run either one of them I get the result:

No protocol specified
Error: unable to open display :0.0

Also, I am running kubuntu 9.10 if this helps.

I am really not sure what is going on here--does anyone have any ideas for troubleshooting this?


Try checking this site here [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Also try configuring your xorg.conf file, make sure to make a back up just incase.

NOTE: Ati Radeon cards do not have any support from AMD anymore, use the open source free ones.

---

### Post by tgalati4 on 2010-04-29
You might need to log out and log back in to restart xorg, or control-alt-backspace (if you have it enabled).

Turn on debugging flags in your program when compiling and run the program in a terminal to capture errors.

---

