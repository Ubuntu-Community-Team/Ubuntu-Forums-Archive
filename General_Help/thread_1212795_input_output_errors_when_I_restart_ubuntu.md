---
title: "input output errors when I restart ubuntu"
date: 2009-07-14
forum: General Help
---

### Post by beagle28 on 2009-07-14
Hello, 

Today, I had to restart my ubuntu (version 8.10) and now I get a lot of input/output errors when i try to restart my computer. The last two errors I get:

init: Unable to execute "/bin/sh" for rc-default: Input/output error
init: rc-default main process (4593) terminated with status 255

I would be very grateful if someone could help me out.

Warm regards,
Céline.

---

### Post by prshah on 2009-07-14
> **beagle28 said:**
> 
Today, I had to restart my ubuntu (version 8.10) and now I get a lot of input/output errors 

Can you boot into recovery mode? In that case, when you get to the prompt, give the command ```
touch /forcefsck
``` and reboot (Press Ctrl+Alt+Del)

When the computer starts up again, it will run a filesystem check. WARNING: There is a potential for dataloss, so you do this at your own responsibility.

---

### Post by beagle28 on 2009-07-14
I tried to do this but I still have I/O errors

I am not able anymore to go back to the safe mode.

---

### Post by prshah on 2009-07-14
> **beagle28 said:**
> I tried to do this but I still have I/O errors
I am not able anymore to go back to the safe mode.

I suggest you boot off a liveCD, then open a terminal (Applications-Accessories-Terminal) and run fsck```
sudo fsck -p /dev/sda1
``` (Replace sda1 with the actual partition id on your system), If you have difficulty figuring out the correct partition ID, post the output of ```
sudo fdisk -l
``` here for more guidance.

---

