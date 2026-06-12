---
title: "Grub 2 editing."
date: 2010-10-22
forum: General Help
---

### Post by thebarisaxkid on 2010-10-22
Oh yay, another Grub question...

So here's my situation.  I have an internal hard drive enclosure (make internal hd's external) I use mainly to fix a desktop pc.  I installed 10.10 onto the hd from my laptop. (the desktop can't boot from usb drive, so yeahh.)  The laptop itself has 10.10 as well as vista.  So when I was installing 10.10 to the hd, it found these two and listed them under grub along with the "real" 10.10.  So now I put the hd back in the desktop and I boot up and see all these OS's listed in the menu.  How can I get rid of these invalid entires? And how can I set it up so that it automatically boots to Ubuntu?

Sorry if it sounds confusing.

---

### Post by Quackers on 2010-10-22
Plenty to get you started in this thread :-)

[http://ubuntuforums.org/showthread.php?t=1541785&highlight=delete+menu+items](http://ubuntuforums.org/showthread.php?t=1541785&highlight=delete+menu+items)

---

### Post by azertyh on 2010-10-22
hello,
perhaps this can help you [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by thebarisaxkid on 2010-10-23
After I added some updates, Grub fixed itself. 

Grub probably updates when you are updating your system. (duh)

Thanks for the links, they should be helpful in the future.

---

### Post by oldfred on 2010-10-23
Your update either installed new kernels or parts of grub2 which triggered an update-grub.

If you just want it to rescan and update menu.

```
sudo update-grub
```

If the drive order changed sometimes this works better as it reinstalls grub to the MBR of the drive you select and stores info to know which drive to reinstall to:
```
sudo dpkg-reconfigure grub-pc
```
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

