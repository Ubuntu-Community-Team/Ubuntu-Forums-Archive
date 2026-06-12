---
title: "Screen saver - multiple versions"
date: 2012-01-04
forum: General Help
---

### Post by msknight on 2012-01-04
This happened on the last few Ubuntu versions and is also happening on the current 11.10 xubuntu.

The screen saver is set to disabled and power management is turned off.

All is good with the world until a reboot.

The system then reverts to what I think are the default settings. 10 minutes and the screens go blank.

Go back in to the screen saver preferences and everything is as I set it.

So, I turn the screen saver back to blank, enable the power management, then turn the screen saver off and then turn off power management again ... and everything is once more fine until the next reboot.

---

### Post by mike555 on 2012-01-04
I also had that problem, I fixed it by   

 open leafpad and save this in your home folder as 
.dpms-off
 

Code:


#!/bin/bash
xset -dpms
xset s off


Right click on the saved file
 Properties > permissions
 and mark Execute 

Then right click on the file and copy.
 Open startup applications and paste the file copy as the command. don’t forget dot .
 
Log out/in and in the terminal run 



Code:


xset -q


to check if dpms is disabled.

---

### Post by msknight on 2012-01-04
Many thanks, I'll give that a try.

---

