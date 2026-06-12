---
title: "Switching Customized Ubuntu to another machine"
date: 2006-03-12
forum: General Help
---

### Post by Trajan on 2006-03-12
I have a bit of an issue;
I have a 120gb drive with ubuntu installed on it (customized completely.) And I recently purchased a new comp. 
Now my issue is that I want to switch out the 120gb HDD which was used in conjunction with another HDD (windows drive that had dual boot with grub installed) so that I can use that drive on my new computer (it's faster).
Is there a way to correctly do this with out reinstalling the whole distro again and with out messing up the installation on the old pc  ? ?

---

### Post by alamba on 2006-03-12
Not sure about this....swapping the HDD into your new machine and reinstalling grub might help. Or is that not an option?

A

---

### Post by Trajan on 2006-03-12
yeah but my issue is that "how can I go about doing this ?" is there a how to ? Since i've never actually done this before (but need to now).

---

### Post by alamba on 2006-03-12
HowTo:
1. Unscrew HDD from current machine.
2. Screw HDD to new machine.
3. Put connectors (wires) to HDD in new machine.
4. Go into BIOS and check if HDD is recognized.
5. Search forum for reinstall grub.

You should be pretty much done! Incase you need help in what wire's go where just check the wires on your current HDD on the new system. There will be a power wire and a data wire.

A

---

### Post by Trajan on 2006-03-12
LOL... I do know how to insert a new HDD in a new machine the only issue is the reinstallation of grub.

---

### Post by alamba on 2006-03-12
Mutiple ways...here are some:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

[http://ubuntuos.com/2006/03/howto-restore-grub.html](http://ubuntuos.com/2006/03/howto-restore-grub.html)

A

---

### Post by Trajan on 2006-03-12
Thanks a bunch alamba. 0_o

---

### Post by alamba on 2006-03-12
no problemo. have fun with your new system.

---

### Post by Trajan on 2006-03-12
Hey I got it working smoothly, but now my issue is that for the grub loader its displaying the old machine's specs (Winblows Xp Home). But on the new machine I have XP Pro installed. How can i edit this since i cant load windows at all if i click the windows link.

---

### Post by WildTangent on 2006-03-12
Simple, edit the grub menu config:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

Make sure it points to the right partition numbers.

-Wild

---

