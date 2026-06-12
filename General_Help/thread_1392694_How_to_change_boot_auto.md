---
title: "How to change boot auto?"
date: 2010-01-28
forum: General Help
---

### Post by grizato on 2010-01-28
I originally had Ubuntu 9.10 desktop. Then I resised the partitio with the ubuntu moblin installer and installed ubuntu moblin remix(which is an interesting little distro!), but now, when I turn it on, it auto highlghts the moblin partition with (boot in 5, 4,3...). I know this is not a bug, it's just a pain.

Does anybody know how I can highlight anther entry?

---

### Post by drs305 on 2010-01-28
Are you using Grub, if so, which version?  Providing us with the information from running the boot info script will give us the information we need:

[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

If you are using Grub 2 and merely need to change the default selection, you can refer to the "G2- Common Tasks" link in my signature line.

---

### Post by grizato on 2010-01-28
It says grub 2. Do I need to give in the whole file?
Does it have any private data on it?

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  


I hope this'll do!

---

### Post by drs305 on 2010-01-28
> **grizato said:**
> It says grub 2. Do I need to give in the whole file?
I hope this'll do!

Well, it might. Since you are using Grub 2, you can run this command to see how many menuentries you have:

```
grep "menuentry" /boot/grub/grub.cfg
```
This should return several lines, all beginning with "menuentry". These should be the same choices you see on your Grub 2 menu.

Count to the one you want to have highlighted, starting with 0. So if you want the second menuentry, that would be counted as 1.

Next open the file that determines the default entry:
```
gksu gedit /etc/default/grub
```

Find the line (the number may be different):
> GRUB_DEFAULT=0
Change the value to the one you determined above. Save the file.

If you want to change the amount of time the menu is displayed (in seconds), you can change the line (again, you may have a different value):
> GRUB_TIMEOUT="10"

Now run:
```
sudo update-grub
```

If this doesn't work or you aren't sure the results of the boot info script would help. It provides us with disk identifications, etc but there is no personal data in the results. Lots of users needing help have posted the contents in these forums.

---

### Post by grizato on 2010-01-29
Thanks!!
:P

---

