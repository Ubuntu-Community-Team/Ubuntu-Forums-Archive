---
title: "PLEASE HELP: MEMTEST86 v2.11 WON'T STOP RUNNING"
date: 2010-12-28
forum: General Help
---

### Post by bolutifeanifowose on 2010-12-28
I recently did an update on my ubuntu netbook. As is routine, it had to restart to save all the changes. But when I did, it began to run Memtest and hasn't stopped ever since. 

Even when I passed the test, it told me to press ESC to continue, but when i did, it would only reboot the computer and restart the Memtest. It's a new netbook. It's been almost a month and I really need my netboook to work again. PLEASE HELP!!!!

---

### Post by rvchari on 2010-12-28
when you get the grub menu, could u find just enough time to select the recover option ? i am not a geek but then i keep trying for ways at the same time take guidance from this wonderful forum

---

### Post by bolutifeanifowose on 2010-12-29
I don't see a grub menu. it simply starts running the test after it boots up.

---

### Post by hawthornso23 on 2010-12-29
If it isn't giving you a choice but is going straight to memtest each time then something is wrong with your grub setup. The first step to fixing the problem is probably to get ubuntu running by booting from a live CD. Once you have ubuntu up and running, you should be able to mount your disk, access the grub files, and have a go at fixing the problem that way.

Edit: You might also be able to get a grub menu by hitting either shift or escape (depending on your version of grub) during bootup. There is typically a very narrow timeslot for hitting the key and getting the grub menu, so often the best strategy is just to spam the key furiously during bootup.

---

### Post by Quackers on 2010-12-29
Before this started, did you edit /etc/default/grub to change the default operating system? Or did you install Startup Manager and change the default OS?

---

### Post by bolutifeanifowose on 2010-12-29
When I get to the grub menu it only gives me the options of: Memory test (memtest86+) and Memory Test (memtest86+, serial console 115200). There is no recover option. 
 
And i don't believe i edited or changed anything nor did i install anything. 
Where do I go from the GNU GRUB?

---

### Post by dcstar on 2010-12-30
> **bolutifeanifowose said:**
> When I get to the grub menu it only gives me the options of: Memory test (memtest86+) and Memory Test (memtest86+, serial console 115200). There is no recover option. 
 
And i don't believe i edited or changed anything nor did i install anything. 
Where do I go from the GNU GRUB?

If there are no kernels in the Grub list then something went wrong with the update.

Try and reinstall Grub:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

