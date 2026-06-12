---
title: "can't reinstall natty"
date: 2011-09-19
forum: General Help
---

### Post by p3aul on 2011-09-19
I had natty installed alongside a corrupt version of Windows. it was on a small partition and I was running out of room so I reinstalled natty and gave it the whole disk(reformatted) thus eliminating windows. But now Natty won't run at all. All I get is a black screen with a blinking cursor. The old install worked just fine. I reinstalled using the same disk. What has happened?
Thanks,
Paul

---

### Post by mörgæs on 2011-09-19
It sounds like you need to add boot options. There are some links explaining how to here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by p3aul on 2011-09-19
Well that thread was all about upgrading. I didn't upgrade, I did a clean install using the whole hard drive. The old install grub worked fine offering the corrupt window choice or the Ubuntu choise. Of course I never chose the Win choice that would have been asking for trouble, as windows would have just wiped out grub. i don't want to go there again. I just want to install Ubuntu 11.04 with a clean install on the whole harddrive without partitioning. I hope some of the old hand gurus here knows the answer, because I have been pulling my hair out(well, I would if I had any hair!) I should mention that the same Live DVD was used in all cases.

---

### Post by staticd on 2011-09-20
1)boot from a live CD
2)mount your boot partiton from the nautilus  side pane. confirm that it has the /boot/grub directory in it. get the path  of the mount point by pressing Ctrl+L . It will be of the form "/media/<random-letters-here>"
3) run
```
sudo grub-install --boot-directory=/media/<partion-uuid> /dev/sda 
```

when you restart, you should get the grub menu.

If this doesn't work try reinstalling.

---

