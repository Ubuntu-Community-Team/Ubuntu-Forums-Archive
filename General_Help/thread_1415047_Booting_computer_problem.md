---
title: "Booting computer problem"
date: 2010-02-24
forum: General Help
---

### Post by LePooks on 2010-02-24
I said other OS. because it's affecting the whole computer. I'm not sure what's happening. But when I start up my computer I get the norm " DELL XPS" loading, then I get the usal black screen, then I get "GRUB loading" and then saying that the computer has nothing to boot with. and underneath it it says. SATA 1: Installed SATA2: Installed and SATA 3 and 4 are not installed.
This happened since I've installed my NAS Harddisk. on the computer (external).

---

### Post by lavinog on 2010-02-24
Does removing the NAS drive restore the system?

Is this grub2 or grub1 (If this was a fresh install of karmic, it should be grub2...if you upgraded from a previous version it should still be grub1)

---

### Post by LePooks on 2010-02-25
It was grub2 and the problem still occures when the NAS is unplugged.

---

### Post by oldfred on 2010-02-25
I do not know about NAS but we will need to see how your system is booting. Run this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by lavinog on 2010-02-25
I don't recall if drive order makes a difference in grub2, but did you change anything in bios, or reverse the order of the drives?
Were you dual booting?  Did the NAS drive require a special driver in windows?

---

