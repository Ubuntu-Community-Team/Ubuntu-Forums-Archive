---
title: "Disable samba passwd sync"
date: 2010-12-12
forum: General Help
---

### Post by stek_87 on 2010-12-12
Hi! I'm having a problem regarding samba..

I want to have a different samba password than the password for the system account. Every time i logon to my linux system with ssh, the samba password for that account gets synchronized with the linux account. How can I get rid ot this behavior?

---

### Post by stek_87 on 2010-12-13
anyone?

---

### Post by Bladeforger on 2010-12-13
From page 78 of Samba 3 by example, free download from the samba website:

> [global]
workgroup = PROMISES
netbios name = DIAMOND
interfaces = eth1, eth2, lo
bind interfaces only = Yes
passdb backend = tdbsam
pam password change = Yes
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*Password* %n\n \
*Re-enter*new*password* %n\n *Password*changed*
username map = /etc/samba/smbusers
unix password sync = Yes

I think the operative line is the unix password sync = yes.  Try changing it?

(This is in your smb.conf file located at /etc/samba/smb.conf.)

---

### Post by stek_87 on 2010-12-13
Thanks for your reply!

My book says "unix password sync: YES causes Samba to change a user´s Linux password when the associated user changes the encrypted samba password"

I will try some other things tonight and will post back if I get rid of my problem.

---

### Post by Bladeforger on 2010-12-13
I installed system-config-samba today and used it to set up the user, user password, and the file sharing today.  It worked.

So if nothing else works, try that!

Keith

---

