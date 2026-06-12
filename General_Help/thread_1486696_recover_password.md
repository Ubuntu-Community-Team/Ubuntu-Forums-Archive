---
title: "recover password"
date: 2010-05-18
forum: General Help
---

### Post by r3koob on 2010-05-18
I am trying to find out why a friends Dell mini is running so slow but he does not know what the admin password has been set to.  I have searched the forums (for days) and from what I can find I need to access recovery mode on boot up but when I hold Esc down during boot up it doesn't give me the recovery mode.  it is 8.04 on a Vostro A90.  any idea's?  I am pretty new to Ubuntu.  Thanks for the help.

---

### Post by nothingspecial on 2010-05-18
Try holding down shift, although in 8.04 it should be escape.

---

### Post by Jakiejake on 2010-05-18
Try The Live CD It may have some tools.
I know you said you can't hold Esc but i'll post these anyway from Ubuntu Geek
Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reboot

---

### Post by snowpine on 2010-05-18
Recovery mode can be a little tricky on the Dells, check it out: [https://help.ubuntu.com/community/DellMini9#Booting%20into%20Recovery%20mode](https://help.ubuntu.com/community/DellMini9#Booting%20into%20Recovery%20mode)

Then follow these instructions to reset the password: [https://help.ubuntu.com/community/DellMini9#Login%20Problems](https://help.ubuntu.com/community/DellMini9#Login%20Problems)

---

### Post by r3koob on 2010-05-18
Thank you snowpine and all... for the info... worked like a charm...

---

