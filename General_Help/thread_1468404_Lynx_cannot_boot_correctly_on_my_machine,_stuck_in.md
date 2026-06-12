---
title: "Lynx cannot boot correctly on my machine, stuck in MemTest86"
date: 2010-05-01
forum: General Help
---

### Post by scratman on 2010-05-01
Hi boys and girls.  I upgraded my 9.10 Ubuntu install last night using the Update Manager, everything downloaded fine, and appeared to install correctly.  When it finished I got the message advising that my machine needed to reboot for changes to take effect.  I checked my mail quickly before rebooting, and then let it do its thing.

It shut down fine, then booted up and went into MemTest86.  No real worries, so I wandered off expecting it to take 10-20 minutes.  After 4 hours, though, I was starting to worry.  A message at the bottom of the screen advised something along the lines that the test had been successful, and I could press Escape to exit.

I did, and my machine rebooted, and went back into MemTest86.  I just figured I was being too impatient and left the test running all night.  My machine has now been running MemTest86 for 16 hours, and while the timer is still running and the tests refreshing, my keyboard is not responding.

Any ideas why this may be?  Should it take this long?  Can I skip Memtest86 and get on with my shiny new OS?  Any help gratefully and humbly received.

Thanks in advance!!! :D

---

### Post by dino99 on 2010-05-01
first time i met this issue, may need some googling.

when it ask for mentest, is it possible to refuse and call a terminal, then

 sudo dpkg --configure -a


if you previously had grub1 installed, you MUST remove/purge all the grub installed packages then install grub-pc and grub-common, and

sudo grub-mkconfig && update-grub

---

### Post by happyhamster on 2010-05-01
Try rebooting into grub: hold the shift key during the early stages of the boot process. This should bring up the grub2 menu, from which you should be able to choose a kernel to boot. It could take a few tries to get the menu to show though.
It's possible that memtest has somehow become the default boot choice: in that case you'll have to do some editing later. 

> 
My machine has now been running MemTest86 for 16 hours,
> 
Should it take this long?
Memtest just runs forever. But at least you can now be sure your RAM is fine :).

---

### Post by scratman on 2010-05-01
Thanks for that! :D  Holding shift let me select the correct kernel to boot from.  Then, once I had got into Ubuntu I went to System > Administration > StartUp-Manager entered my password and selected the correct image in Default Operating System.   Saved the settings, rebooted, and that's sorted it.  Now I just need to get used to all of the new stuff on here!!! :D

---

### Post by irva on 2010-06-28
Hey,
I have the same problem, but i do not manage to get into anyting of what is mentioned above.... I do not get into any terminal, and the boot sequens looks ok (shift did not help, but f2 and f12 gives me setup and boot sequence)

Inga

---

### Post by happyhamster on 2010-06-28
> **irva said:**
> Hey,
I have the same problem, but i do not manage to get into anyting of what is mentioned above.... I do not get into any terminal, and the boot sequens looks ok (shift did not help, but f2 and f12 gives me setup and boot sequence)
You usually have to keep the shift key pressed after the first bootscreen (with the F2 and F12 options) has disappeared. Just keep the shift key pressed. (And for older Ubuntu versions, you'll need to press the escape key.) Good luck.

---

