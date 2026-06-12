---
title: "Forget Login password (URGENT)"
date: 2010-06-28
forum: General Help
---

### Post by vois2009 on 2010-06-28
Hi,
 
I've accidentally change the login password but forget what I've key in.
 
How can I retrieve my password? Now totally can't login at all. Is there any options.
 
Pls HELP. URGENT.
 
Regards,
Ken Tong

---

### Post by oldos2er on 2010-06-28
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by amauk on 2010-06-28
restart machine
at grub (may have to press Esc for grub menu) select to boot in recovery mode
at the menu thing, choose "root shell"

At prompt (replace <user> with username), type
passwd <user>

it'll prompt you for a new password

reboot, & login

---

### Post by aysiu on 2010-06-28
> **amauk said:**
> restart machine
at grub (may have to press Esc for grub menu) select to boot in recovery mode
at the menu thing, choose "root shell"

At prompt (replace <user> with username), type
passwd <user>

it'll prompt you for a new password

reboot, & login
It's changed in recent versions of Ubuntu to be holding down the Shift key during bootup (instead of pressing Escape).

---

