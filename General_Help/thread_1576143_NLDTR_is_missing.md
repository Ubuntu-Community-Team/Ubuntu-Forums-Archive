---
title: "NLDTR is missing"
date: 2010-09-16
forum: General Help
---

### Post by binor2 on 2010-09-16
Hi, I am completely new to linux and ubuntu. I burned the .iso of ubuntu to a DVD-R, and put it in my computer and rebooted it. It seemed to be working fine, but then the installation crashed, and I had to manually turn off my computer. So I took out the CD with ubuntu on it, and now my computer won't start! It says "NLDTR is missing. Press Ctrl+Alt+Del to restart." I can't do anything, because ubuntu never finished installing, and now my windows xp won't run either! It's really scary, if you could offer any advice or help at all, I would appreciate it so much. I'm completely new to this, I'm not even sure if I am posting in the right place. Thank you for reading this, and please, please help!

---

### Post by efosmark on 2010-09-16
This happened to me too. Mine came from a different situation that was unfixable, but in your situation you may be able to fix it by doing the following:

1. Boot into your Windows XP install cd.
2. Go to the repair console (I think you press R at the first menu)
3. Run fixboot and then fixmbr
4. reboot

This should hopefully get you back into XP.

---

### Post by efflandt on 2010-09-16
I think you mean NTLDR (as in NT loader, which Windows sometimes still uses to refer to newer versions).  If you get that error it sounds like you still have a standard MBR and it may simply be a matter of the wrong partition marked as the boot partition (which may be pointing to the incomplete Linux partition instead of Windows partition).  I don't think anything should delete NTLDR.

You could check/fix which partition is marked as the boot partition from gparted on a live/install Ubuntu CD (or similar bootable iso on USB).

---

