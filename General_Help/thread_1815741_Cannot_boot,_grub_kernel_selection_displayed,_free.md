---
title: "Cannot boot, grub kernel selection displayed, freeze after 3 sec"
date: 2011-07-31
forum: General Help
---

### Post by l07 on 2011-07-31
I locked the screen, came back, typed the password, screen remained black, though cursor was visible and moving. Nothing I could do to rejuvenate the screen. Had to switch to tty6, sudo shutdown -r now. Then, on reboot obtained kernel selection, it proceeded to displaying kernel messages, but froze on sdb, after 3 secs. I figured it was the usb, so turned off, removed usb cables to external hard drives, but again it froze saying something about firewire mouse, the mouse is also usb. I tried several times, but no matter what kernel I chose, I couldn't get it to boot. So I loaded puppy live cd, but now it can't access some parts of the disk. I was running utorrent and the folder with partially downloaded files can be accessed but there's nothing there (there was), and some folders can't be accessed at all.
I think something might be wrong with the hard drive, but I hope it's ok.

Please help me boot and access my files.

---

### Post by l07 on 2011-07-31
Hooray! It lives! I thought it could help to use the middle end of the 40 pin connector, because the end I've been using a lot, and disconnecting it by leveraging the sides to take it out. I think that could've contributed to the wires losing contact with the hard drive. Then I booted up, and beheld the error check. Errors were found, pressed f to fix. Said couldn't mount /tmp, so I said s to skip, it rebooted and everything works now! I can even access all of the disk.

Conclusion: when you design a cable, think about how to make it so taking it out doesn't damage it.

---

### Post by searchfgold6789 on 2011-07-31
Damn IDE.....

---

