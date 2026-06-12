---
title: "CIFS VFS error connecting to socket"
date: 2010-08-13
forum: General Help
---

### Post by ncpokrt on 2010-08-13
I am posting this in case it helps someone with the same problem.

I am using Lucid.  I moved computers around and the one I began using could not see the rest of the network; although the other computers on the network could see it.  When booting I would get the message "CIFS VFS error connecting to socket.  Aborting operation." and "CIFS_mount failed".  I tried some fixes from the forums that did not work.  Finally, I looked at /etc/fstab on one of the other computers and I found that there were some lines on the misbehaving computer:


The server samba share
\\\\192.168.1.100\\data	/media/server_public	cifs	guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
/tmp/hfsimage /macdisk hfs defaults,noauto,user,loop 0 0

I commented them out and rebooted.  All is good now.

---

### Post by utonium01 on 2012-07-25
> **ncpokrt said:**
> I am posting this in case it helps someone with the same problem.

I am using Lucid.  I moved computers around and the one I began using could not see the rest of the network; although the other computers on the network could see it.  When booting I would get the message "CIFS VFS error connecting to socket.  Aborting operation." and "CIFS_mount failed".  I tried some fixes from the forums that did not work.  Finally, I looked at /etc/fstab on one of the other computers and I found that there were some lines on the misbehaving computer:


The server samba share
\\\\192.168.1.100\\data	/media/server_public	cifs	guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
/tmp/hfsimage /macdisk hfs defaults,noauto,user,loop 0 0

I commented them out and rebooted.  All is good now.


Thanks ncpokrt! I was having this exact issue and your post was very helpful

---

