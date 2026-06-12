---
title: "Change Resolution of Emulated Ubuntu"
date: 2010-09-21
forum: General Help
---

### Post by alexgeek on 2010-09-21
I'm emulating Ubuntu on VirtualBox, how can I change the resolution of my emulated Ubuntu?
There's no settings in VirtualBox, the System>Preferences>Monitors window has no options to change and I have no xorg.conf.
What is a man to do? 
Thanks

---

### Post by bodhi.zazen on 2010-09-21
You have to install the virtualbox additions in the guest (not the host).

First install build-essential

```
sudo apt-get install build-essential
```

Then follow the rest of these steps

[https://help.ubuntu.com/community/VirtualBox/SharedFolders#Required:](https://help.ubuntu.com/community/VirtualBox/SharedFolders#Required:) Virtualbox Guest Additions

---

