---
title: "un-automount windows partition"
date: 2010-01-28
forum: General Help
---

### Post by winchendonsprings on 2010-01-28
I installed ntfs-3g awhile back to have access to my windows partition. ever since then it automounts on start up.

Is there a way to NOT have it automount on start up?

---

### Post by aust77 on 2010-01-28
You are not clear enough. What exact method did you use to automount? Did you simply install ntfs-3g or did you run certain commands/edit certain files? 




aust77

---

### Post by winchendonsprings on 2010-01-28
I don't believe I performed anything to have the partition automount. Ever since I installed ntfs-3g it has automounted. Also to to unmount it I have to do it from the terminal with root.

EDIT- I have ntfs config. Is there a way to disable the automount with that?



Also how do i edit the thread so it doesn't say [solved]? i meant to say ubuntu

---

### Post by winchendonsprings on 2010-01-28
bump

not solved

---

### Post by john newbuntu on 2010-01-28
Check if you have a line in the file /etc/fstab that is something like:
```
/dev/sda1 /mnt/windows ntfs-3g defaults 0 0
```
(Note that some of the options you see might be different.)

Now comment this line:
```
#/dev/sda1 /mnt/windows ntfs-3g defaults 0 0
```

If you do not find this line, go to system->admin->users/groups. Click on "click to make changes", enter password.  Highlight user name, click properties and go to "user privileges" tab and uncheck "mount user space filesystems".

If this does not work either, please paste the contents of the file /etc/fstab.

---

### Post by winchendonsprings on 2010-01-29
I had this line in the fstab file

/dev/sda1 /media/WinXPx64_internal ntfs-3g defaults,locale=en_US.UTF-8 0 0

so I commented it out. I have not restarted the computer yet. 

So you recommend commenting out this line over this option > "go to system->admin->users/groups. Click on "click to make changes", enter password. Highlight user name, click properties and go to "user privileges" tab and uncheck "mount user space filesystems"."?

---

### Post by john newbuntu on 2010-01-29
Yeah.  Just comment(you may have to use gksudo gedit), save, reboot.

---

