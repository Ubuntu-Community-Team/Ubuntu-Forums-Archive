---
title: "what package do I need to install to get this?"
date: 2010-09-09
forum: General Help
---

### Post by amlucent23 on 2010-09-09
opensuse machines automatically show up in the "My Network" folder of nautilus.  They show up as SFTP servers.  I assume they are using avahi/bonjour service to do this but I dont know what I need to install or how to set it up (which .conf files I can modify to attain this) so my ubuntu systems do the same.

attached is a screen to illustrate exactly what I am talking about

---

### Post by NearlyALaugh on 2010-09-10
If you want the Ubuntu machine to be accessible to other computers on your LAN, **openssh-server** is probably what you want:

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

---

### Post by amlucent23 on 2010-09-10
> **NearlyALaugh said:**
> If you want the Ubuntu machine to be accessible to other computers on your LAN, **openssh-server** is probably what you want:

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

I have ssh installed.  I am looking for a way to make this server easily browsable so my wifes ubuntu netbook will see it.  I want it to use whatever packages and config that the suse server uses.

I know samba would kind of work.. but this seems more elegant.

---

### Post by amlucent23 on 2010-09-11
Bump

---

### Post by sikander3786 on 2010-09-11
So you want to share folders on the network. Not difficult to accomplish with either [Samba]("https://help.ubuntu.com/community/SettingUpSamba") or [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

Setting up either way will make it show up in My Network. Samba is intended for a mixed network of Windows and Linux and NFS only for Linux networks. Go through the links and post back if any queries.

---

