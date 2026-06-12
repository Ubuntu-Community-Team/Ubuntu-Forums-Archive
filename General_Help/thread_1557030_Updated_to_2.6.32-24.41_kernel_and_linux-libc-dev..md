---
title: "Updated to 2.6.32-24.41 kernel and linux-libc-dev. Kernel Panic, Restarts, Grub Error"
date: 2010-08-20
forum: General Help
---

### Post by talent03 on 2010-08-20
Eee PC 1000
Fully updated
Ubuntu 10.04 (lucid)
Netbook Remix

Updated to 2.6.32-24.41 kernel and linux-libc-dev

When I updated and restarted the computer just minutes ago I got a Grub error. File not found. Shutdown and restarted and it booted to login screen and it restarted on its own. It continued to do this about 10 times. The one time I had enough time to force install the previous linux-libc-dev and it stopped. I don't know which is the culprit, the image or libc-dev but when they are installed together my computer is giving random error after error. I tried fully removing and reinstalling the packages but I keep getting the same problems. 

I don't know how to diagnose the errors as it is different almost every time and I don't really see anything significant in the logs. I am currently on vacation in Spain so it may take me a bit to keep updated on this. Any help or news about this?

---

### Post by DieselDragon on 2010-08-20
> **talent03 said:**
> Updated to 2.6.32-24.41 kernel and linux-libc-dev

When I updated and restarted the computer just minutes ago I got a Grub error. File not found. Shutdown and restarted and it booted to login screen and it restarted on its own. It continued to do this about 10 times...

Any help or news about this?I can't shed any light on this alas, but I'm wondering if it might be a post update gitch? 
 
I just updated this system (Standard PC, Ubuntu 10.04 LTS) to the 2.6.32-24.?? kernel via the Ubuntu update manager (The default boot image is now *vmlinuz-2.6.32-24-generic*) and after restarting, re logging and starting Firefox, the system hung completely. I had to do a hard power-down and restart as a result. 
 
It seems to be behaving itself *now* after the subsequent restart...But I'm wondering if anyone else has experienced this?

---

### Post by talent03 on 2010-08-20
I just removed everything associated with v2.6.32-24 and downloaded and reinstalled. I will report back if I am still having the problem.

---

### Post by talent03 on 2010-08-20
Errors and events delimited by blank line:

free magic is broken at 0xe8240489:0xffffffff
Aborted. Press any key to exit
(2 restarts)

error:unknown filesystem
grub rescue>
(4 restarts)

null in the ring
Aborted. Press any key to exit
(2 restarts)

error:unknown symbol type "13"
(3 restarts)

Pressed ESC and random keys... booted, logged in, forcefully restarted.

Booted again, mouse froze and force installed old version of linux-libc-dev with keyboard

Stack trace
Kernel panic - not syncing: Fatal exception in interrupt
PID 0, comm: swapper Tainted G  D  2.6.32-24-generic #41
call trace [<c058a766>] ? printk + 0x1d/0x1f
(restart)

could not write bytes: Broken pipe.

Booted, reverted to old kernel and linux-libc-dev. Working again.

](*,)

---

### Post by talent03 on 2010-08-20
I updated fully again, since I suspected it was maybe a corrupt grub config file. I did the command update-grub. Once I did this, when I restarted I did not get anymore errors. I will report back if there are any more issues regarding this; for now, I marked the thread as solved.

---

