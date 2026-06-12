---
title: "Ubuntu server install issue"
date: 2011-07-20
forum: General Help
---

### Post by Nekew on 2011-07-20
im installing ubuntu server, and when it asked what server components i wanted installed (ie Mail Server, DNS Server ...), i bumped a key (not sure what) and it just went on with the installation with no server components selected. will i be able to go back and install these, things?

---

### Post by papibe on 2011-07-20
Sure you will, you can install the packages yourself using apt-get or using [tasktel]("https://help.ubuntu.com/community/Tasksel").

BTW, if you haven't done any more work, update, etc on the server, just reinstall it again. No harm done.

Regards.

---

### Post by Nekew on 2011-07-20
I cant ssh into it (prolly my fault) to use apt-get so ill prolly end up just reinstalling. thanks!

---

### Post by tgalati4 on 2011-07-20
man tasksel
sudo tasksel

---

### Post by 2F4U on 2011-07-21
You need to install ssh server if you want to be able to login using ssh from your client.

---

