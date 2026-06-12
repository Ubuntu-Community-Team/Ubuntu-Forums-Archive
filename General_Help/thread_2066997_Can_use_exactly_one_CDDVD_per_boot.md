---
title: "Can use exactly one CD/DVD per boot"
date: 2012-10-05
forum: General Help
---

### Post by tetsuo29 on 2012-10-05
Please help. I've been searching and searching (must not be figuring out the right search terms) and I can't find a solution to my issue.

The problem is that I can only use one CD or DVD per boot.

Example:
- reboot
- open DVD drive tray
- insert disc
- use disc normally
- eject disc
- close empty tray
- now, I can NEVER get the tray to open again until I reboot, hardware eject button on drive doesn't work, can't get the eject command to work

I've tried variations of the eject command:
- eject
- eject -r /dev/sr0
- sudo eject -r /dev/sr0
- eject -r
- gksudo eject /dev/cdrom1
- gksudo eject /dev/sr0

I really find it inconvenient to have to reboot in order to be able to insert more than one CD or DVD into the drive. I'm hoping someone out there has the solution. Thanks in advance for your help.

---

### Post by tetsuo29 on 2012-10-06
So, after a whole lot of additional Google-ing, I've found a (somewhat clunky) solution:

- eject -i off /dev/sr0

Which produces the message:

CD-Drive may be ejected with device button

And, of course, I can then press the button on the drive and it will open. This has got to be a bug. There must be some way to be able to open the empty drive without needing to enter this command each time.

---

