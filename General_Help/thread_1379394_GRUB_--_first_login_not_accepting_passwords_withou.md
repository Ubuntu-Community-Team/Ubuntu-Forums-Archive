---
title: "GRUB -- first login not accepting passwords without problems"
date: 2010-01-12
forum: General Help
---

### Post by Dogalot on 2010-01-12
Hello,

I am having an issue that I have not been able to find how to fix.  If there is a link to go to - please reply with it...  The issue is this...  I am running Karmac (edubuntu version) After GRUB, the first log in screen appears...  I can type my password in about 15 - 20 times before it realizes I typed in the correct password.  Sometimes it even starts to load the desktop screen and then bombs back to the first log in screen.  After I eventually get logged in -- anytime there is a need for the password (installed something, or changed some setting requiring the password confirmation) - no problem -- it's accepted the first time it is typed.  I don't know if gnome has the issue, because it seems if I change to 'xfce' it doesn't take as many times to get in...

Does anyone know what is happening and how to fix it?  I have not tried the "sudo password fix" I found from psychocats...fixsudo... but that seems the closest thing to try...  Any more direct fix?  Any suggestions would greatly reduce my frustration level...  And would be greatly appreciated!

---

### Post by Dogalot on 2010-01-14
> **Dogalot said:**
> Hello,
 After GRUB, the first log in screen appears...  I can type my password in about 15 - 20 times before it realizes I typed in the correct password.  

The issue hasn't been solved, but the work around a friend and I came up with was to downgrade the gnome display manager from 2.28 back to 2.20.  

[http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html)

It at least works now...  Thanks Ken!!  :D

---

