---
title: "Bootable USB not getting detected after kernel messup"
date: 2011-10-05
forum: General Help
---

### Post by Sapta on 2011-10-05
I had installed Ubuntu using Wubi and yesterday, I tried adding a patch to the kernel and recompile. What happened is available space went to 0 and the process aborted giving some errors. 

I could no longer log-in in the gui mode as it was saying gnome power-manager was not set up properly. I tried creating some space using generic mode root log-in but couldn't. Finally, I backed up some files and uninstalled ubuntu from within vista. 

Now, I have a bootable usb with ubuntu installed which I tried to use to backup/create space. But I couldn't boot using it ever since that problem occurred. I hoped it would get solved if I uninstall ubuntu but it's still persisting. What should I do to fix the problem?

The error I am getting is "No boot sector found"

---

### Post by westie457 on 2011-10-05
Is the error 'No Boot Sector Found' displayed when booting your main hard drive or only whrn booting from your USB drive?

---

### Post by Sapta on 2011-10-10
The error message comes up only when I try to boot from a bootable usb. I tried 2 so far. Both gave the same error.

Boot from hard drive is working perfectly fine. Can't try a live cd/dvd because my dvd-writer is broken.

---

### Post by wildmanne39 on 2011-10-11
Hi, have you gone into setup and set your usb stick to boot first before your hard drive?

Have you tried the usb stick on another computer to confirm that there is not something wrong with ubuntu on the usb stick?

How did you create the usb stick did you burn it and not just copy it?

What program did you make the usb stick with?

I use startup disk creator in ubuntu and I have to install the boot loader after it gets through creating all the other files so it is a separate step.
Thank you

---

### Post by bcbc on 2011-10-11
Compiling a kernel takes a surprisingly large amount of space. When I did it it was about 7 or 8 GB. That's not including the source etc.

I would suggest recreating the USB - obviously something is wrong with it. Installing and uninstalling wubi cannot affect the boot sector on your USB or the ability to boot from it.

---

