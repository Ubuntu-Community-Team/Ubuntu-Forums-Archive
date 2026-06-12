---
title: "Virtual box in ubuntu, help!!"
date: 2009-10-24
forum: General Help
---

### Post by Camilia on 2009-10-24
I have been trying to set up virtual box in ubunut for windows. In accessories I have virtual box. I click on new and follow the instruction. Then insert windows restore CD and click start. I get the message that No bootable medium found. What else can I do?

I need this to read a CD for college book.

---

### Post by shaggy999 on 2009-10-24
If you're trying to use a "restore cd" inside virtualbox most likely this will NOT work. "Restore CD's" are OEM discs that are generally tied to a particular manufacturer. When the CD boots it checks the motherboard's BIOS and checks if it's "Dell", "Compaq", "HP", etc. When you boot in Virtualbox you get an emulated virtualbox BIOS. More than likely you're running down a dead end.

As for mounting CDs, You will need to make sure that the settings for the guest image point the virtual CD to your CD-ROM drive, usually /dev/cdrom. You have to edit this while the machine is turned off (right-click the guest and click "settings". There should be a dedicated CD-ROM tab on the page that pops up. Then when virtualbox boots up there is an icon on the bottom right of the window that looks like a CD. Right-click it and click "mount" or something similiar.

---

### Post by Camilia on 2009-10-24
> **shaggy999 said:**
> 
right-click the guest and click "settings". There should be a dedicated CD-ROM tab on the page that pops up. Then when virtualbox boots up there is an icon on the bottom right of the window that looks like a CD. Right-click it and click "mount" or something similiar.

I did as you suggest. I get the option to boot from CD. I get Could not read boot medium. Now trying it with the windows restore disk. It is starting up.

---

### Post by MelDJ on 2009-10-24
did you mount your host cdrom?

---

### Post by Camilia on 2009-10-25
> **MelDJ said:**
> did you mount your host cdrom?

I think I did. I changed the settings in the virtual box. Is that what you mean.

The restore CD almost worked. It has been stuck for 15 on last load up.

---

