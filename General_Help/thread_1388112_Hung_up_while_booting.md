---
title: "Hung up while booting"
date: 2010-01-22
forum: General Help
---

### Post by grouchotron on 2010-01-22
I recently installed Ubuntu on my computer, and today after hooking up the internet for the first time it asked me to update. I clicked install, then restarted the computer.
 
While booting up it hangs up after the following is displayed:
 
fsck from util-linux-ng 2.16
/dev/sda1: clean, 149460/2400256 files, 984175/9582764 blocks
 
I've tried ctrl-alt-delete, it restarts, asks me how I want to reboot, and whether I choose generic or recovery mode it still hangs up here.

---

### Post by ajgreeny on 2010-01-22
Is it actually doing a disk check (fsck) as seems possible?  Try booting again, but when you get to the grub menu, highlight the kernel you are booting and hit "E" to edit, scroll to the line ending with "quiet splash" and delete those two words.  Hit enter to accept the edit and then "B" to boot to a text boot (this time only, don't worry) and you may find that the system really is doing a check, which can take a long time.

If all this gets you nowhere, try booting to an older kernel from grub, assuming you have one.  We can then try and sort out your problems.

---

### Post by grouchotron on 2010-01-22
Thanks for the reply!

---

### Post by saewelo on 2010-01-23
I am using the netbook remix of ubuntu and I have the same issue.

The system tries to run fsck as scheduled but it does not start.
This is on a Compaq Mini 110C - it is the only system of the 5 I have ubuntu on that is doing this.  However, the hardware is different on each of the other systems so I am unsure if I am dealing with a Netbook remix bug or a hardware bug.

I am considering dual booting another distro to see if the same issue occur but I had a nasty time setting up the broadcom wireless card in this mini so I'm really not in a hurry to try.

Eventually powering the system off and on 3 times allows it to boot up correctly.

---

### Post by ajgreeny on 2010-01-23
OK, sorry , but this is probably my ignorance of grub2 on karmic.  I thought you could edit the menu on the fly as you could legacy grub, but perhaps you can't do that any more.  Regrettably I will have to admit defeat at the moment on this problem and let you await further answers from others who know grub2 better than I do.

---

### Post by grouchotron on 2010-01-24
I eventually solved my problem by reinstalling ubuntu from the disk.

---

