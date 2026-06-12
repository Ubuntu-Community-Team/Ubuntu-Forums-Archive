---
title: "How to remote log into ubuntu"
date: 2010-08-04
forum: General Help
---

### Post by yuracrazy on 2010-08-04
I have a server that I use to download torrents and to hold files for the rest of my house. The only problem is, I have to log into the machine in person every time or else vnc viewer isn't able to connect when the machine first starts up. Is there anyway I can change this, or am I going to have to connect a keyboard and monitor to this machine everytime?

---

### Post by Ocxic on 2010-08-04
Auto login?  VNC in a remote desktop viewer, if your not logged in there is no desktop to view.

I would recommend you login then lock your screen, after that you can VNC to the machine, and unlock it, then lock it again before you close the session on VNC.

---

### Post by GoldenSun on 2010-08-05
I would just make it a headless server.
Log in over ssh, and transfer files over sftp on filezilla.

---

### Post by dcstar on 2010-08-05
> **yuracrazy said:**
> I have a server that I use to download torrents and to hold files for the rest of my house. The only problem is, I have to log into the machine in person every time or else vnc viewer isn't able to connect when the machine first starts up. Is there anyway I can change this, or am I going to have to connect a keyboard and monitor to this machine everytime?

There are HOWTOs around on how to configure VNC to run without a console login, search them out.

---

### Post by celldweller1591 on 2010-08-05
You can give a try to [Teamviewer in Ubuntu ]("http://ubuntuforums.org/www.linoob.com/2010/05/teamviewer-comes-to-ubuntu/")for remote desktop connection.

---

