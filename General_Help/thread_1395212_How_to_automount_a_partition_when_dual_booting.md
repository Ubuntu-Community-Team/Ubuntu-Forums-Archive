---
title: "How to automount a partition when dual booting?"
date: 2010-01-31
forum: General Help
---

### Post by schwabdale on 2010-01-31
I installed Ubuntu 9.1 side by side with 7. I partitioned the drive to be C: and D:  I would like Picassa to pull pictures from my windows side of the mix. 

However, I have to mount the drive first, then it will allow me to do it. 
Can someone tell me how to do this automatically.

When I double click the file system... it says authentication is required. I put in a password and it works. Just not on startup.


Any help would be appriciated

---

### Post by Leppie on 2010-01-31
the easiest way to do this is like this:
- put yourself in the  fuse group:
```
sudo adduser <username> fuse
```
- install ntfs-config:
```
sudo apt-get install ntfs-config
```
it will launch a configuration script showing you 2 screens, it's very easy to set up.

access the drive without having to type in any password ;)

---

