---
title: "Cannot access SAMBA shares"
date: 2010-05-01
forum: General Help
---

### Post by linuxman94 on 2010-05-01
Hello all,

Whenever I try to access a samba share via nautilus, I get this error:

[[IMG]http://img718.imageshack.us/img718/1997/59236596.png[/IMG]](http://img718.imageshack.us/i/59236596.png/)

I am at a loss of what to.  It use to work, but one day it quit on me.

I had this problem in 9.10 as well.

---

### Post by Morbius1 on 2010-05-01
Is nautilus trying to access an authenticated share and did you tell nautilus to remember the username and password forever?

If so then you might be the victim of this bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267)

The workaround mentioned in that bug report deletes the saved username and password so you'll have to authenticate manually. To find the saved username and password:

Applications > Accessories > Passwords and Encryption Keys > Passwords Tab

Expand the "Passwords: login" entry and you should see the the entry for the remote share.

---

### Post by linuxman94 on 2010-05-01
That was it.  I guess I'll just authenticate manually from now on.

---

### Post by Ginsu543 on 2010-05-01
I was able to get around this issue by simply doing the following:
1) Open Terminal
2) sudo gedit /etc/hosts
3) Add the IP address and name of the samba share you are trying to access, like this:

198.162.0.xxx   Miniserver

After saving the file, I was able to access the samba share using the Network tab in Nautilus or using the Location bar by typing in smb://miniserver/name_of_shared_folder.

---

