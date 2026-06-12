---
title: "Old boot menu reappeared by itself"
date: 2012-05-11
forum: General Help
---

### Post by Oldhacker on 2012-05-11
Using Ubuntu 12.04 AMD64

After all of the problems that I had getting the boot menu organized and corrected so that I could again have access to Ubuntu 11.10 as well as the new addition of Ubuntu 12.04, the boot menu was cleaned up and extranious entries no longer present.

Then, when I turned the computer on this morning, the old boot menu with the plethora of entries was back! Was there a gremlin at work during the night?
Should I just run "sudo update-grub" again and hope that it restores the grub menu?

---

### Post by kc1di on 2012-05-11
how did you originally change the file and save it?
and what file did you change?
if you have unwanted kernel entries the best way if they are no longer needed is to uninstall them.

---

### Post by wojox on 2012-05-11
Did you recieve Grub2 updates recently?

You can run ```
sudo update-grub
```

---

### Post by grahammechanical on 2012-05-11
May I suggest that you install this excellent utility?

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

If you have already got it installed and have used it to make these changes, then you can try this as a possible solution.

After making the adjustments and clicking save, go to the File menu and select Save to MBR. That could be the reason why the changes are not showing up in the Grub menu.

Regards.

---

### Post by Oldhacker on 2012-05-11
I installed the Grub customizer and easily cleaned up the grub menu. On a previous edition of Ubuntu I do recall using this tool.

Thanks

---

