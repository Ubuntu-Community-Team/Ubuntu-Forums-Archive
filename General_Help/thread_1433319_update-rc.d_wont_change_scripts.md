---
title: "update-rc.d wont change scripts"
date: 2010-03-18
forum: General Help
---

### Post by dnoyeb on 2010-03-18
I am using Ubuntu 9.4 called Jaunty Jackalope I think.  Well I know its 9.4.  Anyway, the command update-rc.d **will not** modify existing scripts.  It will only write them all, or remove them all.  I can not for instance do a 

sudo update-rc.d gdm start 30 3 .

where rc3.d is empty or not, and expect a link added to rc3.d.  It won't happen.  The only way I can make **any** change is to first force removal of **all** links, then execute the command.

Does anyone know why this is?

---

