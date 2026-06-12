---
title: "new laptop"
date: 2012-02-11
forum: General Help
---

### Post by Homunculi on 2012-02-11
got a new laptop and was trying a install of ubuntu  while doing the set up i went to name the computer  and missed a key  i did not think it would matter too much but it is the same name as my home computer  
well i got all the drivers and updated 

is there a way to rename the host without reinstalling ...  or do i just have to suck it up and reinstall  ???

---

### Post by yetiman64 on 2012-02-11
You can change the hostname by altering 2 files as root, /etc/hostname and /etc/hosts.

```
gksu gedit /etc/hostname /etc/hosts
``` -opens both files in a root editor.

Find your current hostname in both those files, with the cursor drag a selection over them and type in your new hostname (or just insert a letter or so). Don't alter the formatting in /etc/hosts when putting in the new name. Save both files and exit gedit.

Then in terminal;
```
sudo hostname -F /etc/hostname
``` sets the changes without need to reboot.

Close the current terminal, then reopen, the change should now show in the terminal prompt.

---

### Post by Homunculi on 2012-02-11
thanks ... worked like a charm ... 

now i just ned to sync the 2 home folders and i am good to go ...

---

