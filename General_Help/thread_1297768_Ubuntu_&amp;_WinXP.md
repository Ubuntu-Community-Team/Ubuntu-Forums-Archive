---
title: "Ubuntu &amp; WinXP"
date: 2009-10-22
forum: General Help
---

### Post by Quarkrad on 2009-10-22
I have persuaded a friend to leave winXP and migrate to Ubuntu - so I am soon to have their laptop to rebuild.  They use a small number of windows dependent apps so I will create 'x' partitions and give them a duel boot system.  Although I have done this a number of times (on my machines) I am a little confused re the benefits of what OS to put on the first partition and where grub resides. Does it really matter on a machine (i.e. laptop) where there is only one HD?  (To date I tend to put Ubuntu on the first partition, winXP on the second and have SWAP on a small partition which is the last partition on the HD.

---

### Post by P4man on 2009-10-22
I think XP has trouble booting from anything but the first partition, so put xp there.  But you shouldnt even worry much about it, as you can just isntall XP first, then ubuntu and the installer will figure it all out for you.

That said, are you sure dual boot is the easiest solution for them? Id test those windows apps on wine first, and if that fails, consider a virtual machine like virtualbox. If they have enough ram (1GB at least) then its so much more convenient than dualbooting.

---

### Post by radu.ro on 2009-10-22
If you really need to have a dual boot set-up, depending on your Linux experience, I would suggest installing Ubuntu first, then Windows and then reinstalling GRUB. The logic for this is pretty simple: the data on the hard disk that is most far away from the centre of the platters will have the best read/write speed. In some tests it has been proven that the differences between the speeds achieved for data near the edge of the platters and data close to the centre is almost 30MB/s.

Therefore, after you install XP, boot from the Ubuntu Live CD and from the terminal execute the following commands:
```
sudo grub
root (hd0,1)
setup (hd0)
quit
sudo shutdown -r now
```

After reboot you will be able to start Ubuntu. Edit the /boot/grub/menu.lst file to allow Windows to be chosen in the boot menu.

As P4man suggested, try first to see if those Windows dependent apps can't be run on Wine. Afterwards maybe you should consider building an XP virtual machine (only if your buddy has enough RAM). Only if all these fail, do the dual boot setup.

P.S.: Sun's VirtualBox rocks!

---

