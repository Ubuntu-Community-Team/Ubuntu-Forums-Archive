---
title: "Automount internal drive"
date: 2009-06-26
forum: General Help
---

### Post by John Long on 2009-06-26
Every time I log into my system after a reboot or shutdown I need to open my data drive before it mounts. Is there a way it can automatically mount when I log in?

I'm having a problem with programs looking for the extra drive at login and not finding it and producing an error.

Thanks!

---

### Post by DeMus on 2009-06-26
> **John Long said:**
> Every time I log into my system after a reboot or shutdown I need to open my data drive before it mounts. Is there a way it can automatically mount when I log in?

I'm having a problem with programs looking for the extra drive at login and not finding it and producing an error.

Thanks!

This data drive is it a linux drive or an old Windows drive you like to use?

---

### Post by John Long on 2009-06-26
It's formatted as NTFS, I use it for both Vista and Ubuntu.

---

### Post by DeMus on 2009-06-26
> **John Long said:**
> It's formatted as NTFS, I use it for both Vista and Ubuntu.


**_Auto mount Windows disks_**
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

### Post by tjpren on 2009-10-04
Hello,

Just googled for this very question - great answer, worked like a treat.  Thanks

---

