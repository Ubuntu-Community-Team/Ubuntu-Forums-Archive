---
title: "Virtual disk drive not recognized by wine"
date: 2010-07-20
forum: General Help
---

### Post by dai_vernon on 2010-07-20
I am trying to run You Don't Know Jack in wine - appdb says it has Platinum status, so compatibility shouldn't be the issue.  My laptop doesn't have an optical disk drive.  So, I ripped the disk to an iso image, mounted it with gmount-iso, and tried to open the program.

The program still says the disk is not inserted.  I know on previous laptops with optical drives, I could mount an image on /dev/cdrom0 or /dev/sr0 or whatever and it would be recognized.  My /dev directory had no cdrom0 directory, so I made one.  I mounted the iso there but it still didn't recognize it.  I've tried in my home folder, in /cdrom, and in my newly-created /dev/cdrom0 but no luck.  Anybody know what is going wrong?

---

### Post by dai_vernon on 2010-07-20
I just had to add the folder as a wine drive in wine's configure panel.

---

