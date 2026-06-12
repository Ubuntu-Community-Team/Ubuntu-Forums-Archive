---
title: "Each time I start the computer I have to check the disk"
date: 2011-05-19
forum: General Help
---

### Post by anaximandro on 2011-05-19
When I start the computer I receive the message that the drive that contains the /home partition has an error.
If I press "F" the screen says that the drive is no ready, that I can wait, cancel or manually recovery.
If I wait, in about 1 minute, the system starts normally.
If I press "M" to repair manually, then I press fsck to repair the disk and apparently repairs the disk.
But everytime I start (power on) the computer, Ubuntu always checks the disk and gives a dialog where I can:
press F to attempt to fix the errors, I to ignore, S to skip mounting or M for manual recovery

Any suggestion?. How can I solve this problem?.

---

### Post by anaximandro on 2011-05-20
The problem was that I don't know why, the clock in the bios was reset. When I put the correct date and time, Ubuntu started without any message.

---

