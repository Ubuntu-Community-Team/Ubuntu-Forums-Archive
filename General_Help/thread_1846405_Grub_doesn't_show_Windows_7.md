---
title: "Grub doesn't show Windows 7"
date: 2011-09-19
forum: General Help
---

### Post by cloudpersona on 2011-09-19
update-grub doesn't help. It just shows linux.

---

### Post by fishbulb1022 on 2011-09-19
You might try looking at this thread: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275").


You might also find this page of use: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

I'd recommend trying to reinstall grub2, or reverting to grub legacy. I've had some problems with grub2 before, and reverting to grub legacy seemed to help.

---

### Post by raja.genupula on 2011-09-19
please give me the output of ```
sudo os-prober 
```

---

### Post by cloudpersona on 2011-09-19
/dev/sda1:Windows 7 (loader):Windows:chain

---

### Post by owiknowi on 2011-09-19
just a thought: has the windos partition still set its flag to boot?
you can check this with a bootable cd like parted magic ([http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)).
boot it, start the partitioning tool, select the appropriate partition and it should show 'boot' in its information record.

if not, just right click on it, choose flags from the pop up menu and check 'boot'. update grub as described earlier.

---

### Post by cloudpersona on 2011-09-19
> **owiknowi said:**
> just a thought: has the windos partition still set its flag to boot?
you can check this with a bootable cd like parted magic ([http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)).
boot it, start the partitioning tool, select the appropriate partition and it should show 'boot' in its information record.

if not, just right click on it, choose flags from the pop up menu and check 'boot'. update grub as described earlier.

This was the answer, I bypassed grub and used hiren's cd and loaded straight to windows 7 it gave me a bootmgr missing. Popped in my windows cd and repaired it, did an update-grub and windows 7 showed up.

Thank you all for all the help you gave me.

---

### Post by raja.genupula on 2011-09-19
hey man , we are glad that you have solved your issue . please mark the thread as solved .

---

