---
title: "Feeze on boot..."
date: 2010-06-02
forum: General Help
---

### Post by mvalenti on 2010-06-02
Ubuntu 9.10
Acer laptop


I had an issue with cairo-dock, and tried to remove it via package manager.

rebooted, and screen froze with:

usplash: Setting mode 1152x864 failedf-49e2-a581-20153703c306
usplash: Using mode 1024x768


when I alt-F2, I just get a flashing cursor, no ability to type...

I then tried recovery mode, it scrolls, then freezes at:
init: network-interface (wlan0) post-stop process (916) terminated with status 1

flashing cursor with no ability to type...

I also tried recovering my data (home) with ubuntu one, but only 2 icons in my home dir appeared..

last resort I pulled the drive and hooked it to a DriveWire and to an ubuntu 9.04 machine but could not access due to restrictions...

freeze even...

well... using "try ubuntu" the 2 icons are as follows... Access-Your-Privite-Data.desktop    and the 2nd is   Readme.txt 

Readme.txt contains:

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
"Access your private data"

or

From the command line, run:
ecryptfs-mount-private


cant find the first and error message when trying the second. This is done with an ubuntu one cd on the laptop... I can not access the files this way with laptop hard drive plugged into drivewire on an ubuntu desktop machine.


any help is appreciated!

---

### Post by mvalenti on 2010-06-02
contents deleted

---

### Post by mvalenti on 2010-06-03
bump... help!!

---

### Post by mvalenti on 2010-06-04
help please?

---

### Post by wojox on 2010-06-04
Try putting the hdd back in the Acer laptop. See if it will mount then. You'll have a hard time mounting from a LiveCd. That's the whole reason for encryption. I think if you Google around there is a way to reset it or turn it off.

---

### Post by mvalenti on 2010-06-06
Much appreciated. The hard drive is back in the laptop and still will not boot. I can boot with the live cd, but can not mount the encrypted file. I will continue to google...

---

