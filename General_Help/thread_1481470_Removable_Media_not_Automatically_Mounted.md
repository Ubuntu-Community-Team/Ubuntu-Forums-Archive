---
title: "Removable Media not Automatically Mounted"
date: 2010-05-12
forum: General Help
---

### Post by Joseph Schwenker on 2010-05-12
I use Ubuntu 10.04, and whenever I insert media into a removable media drive, it does not come up on my desktop automatically.  I need to go to Computer, then to the drive.  It then appears on my desktop.  Is there any way to make the device automatically appear?  
This problem occurs for any removable media.  I am using Ubuntu 10.04.

---

### Post by Joseph Schwenker on 2010-05-14
bump

---

### Post by stinkeye on 2010-05-14
From a feed I'm subscribed to it suggests disabling your floppy in the bios will fix this.
[**_[COLOR="DarkRed"]Fix USB Devices Automount Not Working In Ubuntu 10.04 Lucid Lynx[/COLOR]_**]("http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html")

---

### Post by pastalavista on 2010-05-14
Open gconf-editor (Alt+F2->'gconf-editor') and navigate to apps/nautilus/preferences. Make sure the 'media automount' box is checked.

---

### Post by Joseph Schwenker on 2010-05-14
The media automount box is checked.  I'll try disabling the floppy in the bios.

---

