---
title: "Read and Write to USB"
date: 2011-07-18
forum: General Help
---

### Post by kenny_lex on 2011-07-18
I did install QLandkartGT and the plugin to use Garmin with it and it looks like it work, but when I do press "Live Log" I get the error message; "Device Link Error. Failed to request real time position. Realtime thread failed. Failed to configure USB: could not set config 1: Operating not permitted".

I also get a similar error when trying to download tracks; "Failed to download tracks. Failed to configure USB: could not set config 1: Operation not premitted".

My guess is that Ubuntu do not allow programs to use the USB port, so my question is how I do allow this program (or all) to use the USB ports.

---

### Post by dino99 on 2011-07-18
check that "write" is permitted on this hardware

---

### Post by kenny_lex on 2011-07-18
I am a bit noobish just now and do learn Ubuntu/Linux, can you pleas explain how I do that :-)

I did follow this tip, but my /media/ looks empty: "cd /media/ and chmod 0777 -v -R -f usbdevicename".

---

### Post by kenny_lex on 2011-07-18
Update: This may not be the best way to do it, but I did start the program with the command "sudo qlandkartegl", I think I can use the menu edit to insert the sudo before the command line.

---

