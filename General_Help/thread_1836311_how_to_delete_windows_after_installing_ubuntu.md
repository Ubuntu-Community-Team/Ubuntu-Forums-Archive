---
title: "how to delete windows after installing ubuntu"
date: 2011-08-30
forum: General Help
---

### Post by utkarsh009 on 2011-08-30
hi! i installed ubuntu on my computer. but i have windows on my primary boot partition. how do i delete it?

---

### Post by BlacqWolf on 2011-08-30
I've never done this to myself, so I don't know if it works, so try this if someone else on this thread can confirm it works! I'm quite sure it will, though.
 
In Ubuntu, open a partition manager and delete the Windows partition. Then, reboot. When your computer starts back up, hold the 'shift' key, and at the GRUB menu it should open, select Recovery Mode, and when you get to the recovery mode menu, select update GRUB, and then it will scan for installed OSes and update GRUB settings as necessary.
 
Edit: Other people on this thread say it does work, but instead of restarting and entering recovery mode, you can start Terminal and type "sudo update-grub", enter your password and let the terminal do its work (credit to scott_g and pjd99 for the last piece of information)
 
You can also try [kyletstrand]("http://ubuntuforums.org/member.php?u=1016562")'s method, it should allow you use the empty previously-Windows space as your Ubuntu partition.
 
Make sure important information on both your Windows and Ubuntu partition is backed up in case anything goes wrong.
 
I hope you enjoy Ubuntu! :)
 
[SIZE=1](also, if this fixes your problem, please be sure to mark the thread "solved" by using the option in the "thread tools" menu at the top of the thread.)[/SIZE]

---

### Post by scott_g on 2011-08-30
I would update grub before restarting, in case something goes wrong...  I think the command is:
```
update-grub
``` but I could be wrong.

Disclaimer: I've never done this before either, so no guarantees it'll work..

Scott

---

### Post by pjd99 on 2011-08-30
No need to go into recovery mode, delete the partition, then open a terminal and run
```

sudo update-grub

```

---

### Post by kyletstrand on 2011-08-30
Another way to do this would be to created and boot from a Live CD of Gparted.  You could then delete the windows partition and resize your ubuntu partitions to use up the rest of the space.  You can flag the ubuntu partition as a bootable partition also.  Then that should take care of everything.

Remember backup everything important.  As i have done this before and not messed anything up, but that doesn't mean it would give any problems.

---

