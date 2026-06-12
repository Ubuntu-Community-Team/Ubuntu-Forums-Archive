---
title: "problems after enabling desktop cube aspire one"
date: 2011-05-24
forum: General Help
---

### Post by zazione on 2011-05-24
Hello everyone, recently my Acer Aspire One netbook crashed, so I installed Ubuntu 11.04 (couldn't recover windows).
 
It's been great and I'm learning a lot, but I still have a ways to go. ;)
 
Anyways, last night I was downloading software in the Ubuntu software center, and I installed a program called advanced desktop effects, or something like that ... there was something called "desktop cube". I enabled it, which brought up a prompt asking to disable another conflicting process, which I took heed to at first, but eventually I decided to ignore it for some reason to see what "desktop cube" was. After enabling desktop cube, the desktop GUI disappeared (similar to stopping the explorer.exe process in windows). So, I had to restart my computer, and now Ubuntu is loading into a black prompt screen with an unresponsive flashing underscore on the top left.
 
I've been able to load Ubuntu from my SD slot, and I can explore my hard drive this way. Is there a way I can re-enable these processes? Sorry, I cannot remember the names of the ones disabled ...

---

### Post by ivanovnegro on 2011-05-24
Type ALT + F2 and run in the terminal:

```
unity --reset
```This command should go back to the default Unity UI.

The thing is I hope you can login to your system normally and maybe login into Ubuntu Classic and do my suggestion.
The cube is problematic, if you enable it it mostly crashes the UI. But there is also a workaround, you can find it on OMG Ubuntu, a site dedicated to Ubuntu or here in the forums if you search for the Cube in 11.04.
The settings manager you used to do it is called Compiz Config Settings Manager.

---

### Post by zazione on 2011-05-24
Hi! Thanks for the quick response.
 
I've just tried what you've recommended, but my netbook is booting into a debian screen saying basically, "boot regular linux, recovery mode, or memory test". Recovery mode isn't doing anything, it just flashes a sort of debugging screen then stops and becomes unresponsive. When I boot regularly it's just a black screen with a flashing underscore on the top left, and no response to key pressing. I can load an Ubuntu environment by booting from my SD card, and I can access my hard drive in thsi way and use terminal - tried doing unity --reset after navigating to my hard drive's desktop, and it appeared to load a lot of data in terminal, then it flashed error warnings and became unresponsive, though the process was still running when I tried to exit terminal.

---

### Post by ivanovnegro on 2011-05-24
Ok, did you try the option memory test, to assure there is no hardware fault?

---

### Post by Mr. Shannon on 2011-05-24
I don't think running unity --reset in a live distribution will work.  I think you have to boot the installed distribution and run the command from there.

---

### Post by ivanovnegro on 2011-05-24
> **Mr. Shannon said:**
> I don't think running unity --reset in a live distribution will work.  I think you have to boot the installed distribution and run the command from there.

Thats right.
But first the OP has to login somehow into the system.

---

### Post by zazione on 2011-05-24
Ran the memory test,
 
*****Pass complete, no errors, press Esc to exit*****
 
Then system reset.
 
I can enter a command line from the debian boot prompt (GNU GRUB  version 1.99~rc1-13ubuntu3), but 'unity' isn't going to work in there.
 
I can reinstall Ubuntu no problem (I'll know better next time to make a recovery disk etc), it's just a matter of getting the drivers for my netbook ... is there a way to extract them from the original installation? I don't have internet at home, I'm at the library at the moment.

---

### Post by ivanovnegro on 2011-05-24
Of course you could go for a reinstall if that is not a problem as Im not really sure what is the issue.
To install the drivers, an Internet connection would be good.
As a recommendation, do not activate the cube for the beginning.
About the extracting Im not sure, maybe.

---

### Post by dansang on 2011-06-09
To reinstate unity back to previous working order, login as ubuntu from login screen

Press CRt-Alt + T to open a terminal

then use this code to open compiz configuration windows manager

```
ccsm
```

Reselect any unity plugins and reboot.

Your unity desktop should be reinstated after login!

---

