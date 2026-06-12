---
title: "Installed Fedora and didn't configure GRUB = Ubuntu Gone..."
date: 2010-08-19
forum: General Help
---

### Post by MindCalamity on 2010-08-19
I can't get out of this problem now that I installed fedora and didn't configure grub, and also I don't know the id of the partition ubuntu is on can anyone help me ?

---

### Post by Rubi1200 on 2010-08-19
Did you install Fedora after Ubuntu or before?

I have dual-booted Fedora and Ubuntu before without any issues.

Just reinstall GRUB2 and it should recognize Fedora and give you back the boot options.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by MindCalamity on 2010-08-19
Ubuntu was first, but it doesn't work when i choose the Other option from fedora grub... I will try that link now

EDIT: That did it, but now how do I add fedora to the list ?

---

### Post by oldfred on 2010-08-19
Did you do steps 6 & 7? This almost always finds other operating systems.

sudo update-grub

---

