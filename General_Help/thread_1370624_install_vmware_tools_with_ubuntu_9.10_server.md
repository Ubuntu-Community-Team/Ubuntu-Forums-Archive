---
title: "install vmware tools with ubuntu 9.10 server"
date: 2010-01-02
forum: General Help
---

### Post by davidtuti on 2010-01-02
Hi,
could you help me how could I install vmware tools with vmware server 9.1.
I push the option install vmware server but in the /media/cdrom I dont see any package

Any help?
Many thanks and sorry for my english!

---

### Post by darco on 2010-01-02
So the Host is Ubuntu 9.10 server, what is the guest OS?


darco

---

### Post by minuteman80 on 2010-03-25
You have to mount the cdrom manually as Ubuntu Server doesn't. Do it by
$ sudo mount /media/cdrom
Then ls your media/cdrom to see if it worked.

---

