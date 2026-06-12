---
title: "Virtual machine vanished"
date: 2010-03-22
forum: General Help
---

### Post by coyoteboy on 2010-03-22
During an update (last set of security updates I was notified about, on Friday) I lost a virtual machine. Vanished, entirely. Now that was annoying, but not quite as annoying as the fact that the hard drive space set aside for the virtual machine also vanished. The vdi file "containing" the drive vanished, but the space on the drive has not been freed up.I forced an fsck on reboot but nothing was found. I then started erasing other user files to make a little room for something else and while they're erased, their space is not being freed and I can't seem to empty the lost+found.

Anyone know what's going on from that vague set of symptoms?

---

### Post by howefield on 2010-03-22
Have you checked the hidden files in your /home folder for your virtual disk.

The default path to a Virtualbox .vdi is something like

```
/home/user/.Virtualbox/Virtualdisks/machines
```

Open Nautilus by going to the Places > Home menu and press the Ctrl + H keys to view hidden files, scroll down to the .Virtualbox folder and dig down.

---

### Post by coyoteboy on 2010-03-22
Yup, it's not there, and the disk isn't in the HardDisks folder either, only the one I created subsequently (I  checked before making the new one).

Quite baffled by this one, I'd only just finished installing and updating XP when it all went wrong!

---

