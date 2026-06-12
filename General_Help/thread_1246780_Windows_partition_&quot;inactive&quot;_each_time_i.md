---
title: "Windows partition &quot;inactive&quot; each time i boot"
date: 2009-08-22
forum: General Help
---

### Post by mac666 on 2009-08-22
Hey
i have to "activate" the windows partition each time i boot...
By that i mean i have to go to Places > Windows, before i can access my shortcuts to the windows partition.
Ubuntu and Windows shares the same HDD in different partitions.
So no programs, shortcuts or anything may access the Windows partition, before i do that simple action. 
But why?!

---

### Post by apparle on 2009-08-22
Actually the term is mounted and not mounted

Your windows partition is not mounted automatically when computer starts.
And when you goto places and click on it then it is mounted.

To automatically mount partitions on startup you have to configure the file '/etc/fstab'
Here is a good tutorial to configure it
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Tell if you are not able to configure it :)

---

### Post by DeMus on 2009-08-22
> **mac666 said:**
> Hey
i have to "activate" the windows partition each time i boot...
By that i mean i have to go to Places > Windows, before i can access my shortcuts to the windows partition.
Ubuntu and Windows shares the same HDD in different partitions.
So no programs, shortcuts or anything may access the Windows partition, before i do that simple action. 
But why?!

Try this:

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by HiImTye on 2009-08-22
```
sudo apt-get update && sudo apt-get pysdm
```

system > administration > storage device manager

select your partition (should be under sda if you only have one drive)
select your mount point (if it isnt filled in already)
select your option. make sure that 'mount on bootup' or whatever is checked

it will have to be not mounted to work

---

### Post by mac666 on 2009-08-22
damn! i saw Demus post to late... allready began with the fstab, and i think i got it... cannot reboot to try it right now but i think i got it!
Thanks!__

---

