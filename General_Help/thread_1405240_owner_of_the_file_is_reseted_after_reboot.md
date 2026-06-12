---
title: "owner of the file is reseted after reboot"
date: 2010-02-12
forum: General Help
---

### Post by tivrfoa on 2010-02-12
Hi folks!

I changed the owner of the file /dev/lp0, so a normal user can print in this port.
eg: echo "some text" > /dev/lp0

The problem is that today when I started the SO, the owner is root again. :(

How can I fix this?

I think I will add the below script in the /etc/init.d/ folder.

#!/bin/bash

chown leandro /dev/lp0

---

### Post by sandyd on 2010-02-12
> **tivrfoa said:**
> Hi folks!

I changed the owner of the file /dev/lp0, so a normal user can print in this port.
eg: echo "some text" > /dev/lp0

The problem is that today when I started the SO, the owner is root again. :(

How can I fix this?

I think I will add the below script in the /etc/init.d/ folder.
#!/bin/bash

chown leandro /dev/lp0

add your user to the lpadmin group. and the lp group as well.
the /dev is reset by the udev rules each time you restart.

---

### Post by tivrfoa on 2010-02-13
> **carlee said:**
> add your user to the lpadmin group. and the lp group as well.
the /dev is reset by the udev rules each time you restart.
Hey carlee!

Thanks, it's working. The user was already in the lpadmin group, so I just added him to the lp group.
ps: the group lp is not listed in the group list. So I don't know if it existed. Maybe it is just hidden.

When I say group list, I mean: System Menu -> Management -> Users and Groups -> Manage Groups

Well, so it's all fine now. If it stop to work for some reason, I'll let you know. xD

Thanks my friend. =)

---

