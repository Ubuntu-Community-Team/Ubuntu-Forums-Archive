---
title: "Cannot Reboot Anymore?"
date: 2006-06-24
forum: General Help
---

### Post by PBK on 2006-06-24
Hi -

  I installed Ubuntu from the disk and all worked well including rebooting the computer via gnome. I have installed a few programs, but not too many and now when I try to reboot, it just hangs - It seems to get all the way back to the BIOS, but nothing. I have tried removing the extra programs, but that doesn't clear it up. I can then hit the reset button and it starts OK. I can shutdown the computer completely without problems, too. 

  I should probably start from scratch, but before I do, can anyone point me in a direction of what might be causing this? Thank in advance!

Paul

---

### Post by timsch75 on 2006-06-25
if it is getting back to BIOS, I doubt it is a ubuntu problem.

---

### Post by 3rdalbum on 2006-06-25
When you say that it "gets all the way back to the BIOS", do you mean that the X server closes down and the shutdown messages start scrolling up the screen, and the computer hangs at some point there?

Or does it hang just before the messages appear?

I'm having the latter problem. Right now I'm using my old Breezy kernel (which doesn't have the problem) until I can find a solution.

---

### Post by PBK on 2006-06-25
Well - I don't think it's in the BIOS because I'm sure I could reboot before adding extra software. Log file looks somewhat normal, too:

Jun 25 09:16:32 localhost shutdown[7686]: shutting down for system reboot
Jun 25 09:16:41 localhost kernel: [4514195.412000] apm: BIOS not found.
Jun 25 09:16:48 localhost kernel: Kernel logging (proc) stopped.
Jun 25 09:16:48 localhost kernel: Kernel log daemon terminating.
Jun 25 09:16:48 localhost exiting on signal 15
Jun 25 09:18:06 localhost syslogd 1.4.1#17ubuntu3: restart.

  The line "apm: BIOS not found." bothered me, but I have a similar system that reboot ok that also has that line in it.... And it gets past X, 3rdalbum. I don't see it as you describe as this is a remote unit with no monitor attached.

---

