---
title: "ubuntu software center doesn't work"
date: 2011-08-13
forum: General Help
---

### Post by rootnet47 on 2011-08-13
Hi! I'm new to Linux and now I'm using ubuntu 11.10 Oneiric Ocelot alpha 3 . The day before yesterday I was updated my OS by "update manager", at the time of update process had began a popup message informed me that system only can take partial updates and I did so. After that whenever try to install software from "ubuntu software center" the installation does not performed not even asking for the root password. 

Could anyone help me to eradicate such problem?

---

### Post by 3rdalbum on 2011-08-13
How new are you to Linux? If you class yourself as "I'm new to Linux" then the alpha versions are really not for you.

Be careful with "partial updates" in development versions; sometimes a new dependency hasn't been uploaded yet and doing a "partial update" will remove a crucial package because its new dependency isn't available. I tend to use Synaptic Package Manager to "mark all updates" instead of clicking the Partial Update button in Update Manager.

To fix your problem? Try going into Synaptic Package Manager, click Reload, and then after that's finished click Mark All Updates. It'll tell you what packages it will install, remove and update. Check the "remove" part of this list carefully. When satisfied that it's all safe, click Ok and then click Apply.

---

### Post by parthgohil on 2012-08-10
iam not able to ipen my software center either. whether iam unpacking a *.deb or just opening the software center. iam running ubuntu 12.04 and i am super new to ubuntu ! please help

---

