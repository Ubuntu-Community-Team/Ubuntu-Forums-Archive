---
title: "Clearing RAM and Swap"
date: 2006-03-13
forum: General Help
---

### Post by TomAnthony on 2006-03-13
I find if I run Azureus or any other memory intensive program for a long time, the RAM and swap file gets taken up, and remains that way even after I close the application. Is there a command or app that will clear this without having to reboot? Something like FreeRAMXP for Windows.

---

### Post by codejunkie on 2006-03-13
[QUOTE=TomAnthony]I find if I run Azureus or any other memory intensive program for a long time, the RAM and swap file gets taken up, and remains that way even after I close the application. Is there a command or app that will clear this without having to reboot? Something like FreeRAMXP for Windows.[/QUOTE]

I don't know of anything in Linux like FreeRAMXP, but I've noticed in Linux even though it displays a lot of ram or page file usage, if an application needs/requests that ram the OS will free it up, so it can be used by the app that needs it, and not being held by something that is setting there doing nothing. unlike windows if you run an application and then close it, windows seems to only free a very small portion of it, and windows hangs on to the rest. this makes it bad because other things could be making use of it, but it seems to be getting eaten up instead. 

don't know if it would actually help performance any but you can clear the swap space by running 
```
sudo swapoff -a
```
and then
```
sudo swapon -a
```
as for clearing physical ram i don't think you can, because it's controlled by the OS.

---

### Post by TomAnthony on 2006-03-14
Is there any to put this in a batch file so i would just have to click it to do this?

---

### Post by codejunkie on 2006-03-14
[QUOTE=TomAnthony]Is there any to put this in a batch file so i would just have to click it to do this?[/QUOTE]
this should work open a terminal and copy and paste this in there
```
sudo gedit /usr/bin/freeswap
```copy and paste this code into the file
```

#!/bin/bash
sudo swapoff -a
sleep 3
sudo swapon -a
exit

```
save the file and then run
```
sudo chmod +x /usr/bin/freeswap
```
then when you need to clear the swap file, just enter ```
freeswap
``` into a terminal or create a desktop launcher and enter ```
freeswap
``` for the command.

---

