---
title: "Embarrassing chmod accident hoping for a fix"
date: 2009-10-20
forum: General Help
---

### Post by photon5 on 2009-10-20
Short version ---

After messing around with file permissions on my home server, I messed up permissions 1 directory up from root.  I was able to go in and fix my sudo doers file.  After doing so, I went back to fix the remaining files that changed.

Incredibly embarrassing moment ---

While in /lib I accidentally chmod the cpp link.  If you don't know, that evidently is a really really bad thing.  I tried logging from the ubuntu server live cd and fix the link but cpp doesn't appear in the directory nor does cpp-4.1.

Other than a reinstall, is there anything else I can try to rescue my system?   Luckily home directory is on another partition and I back it up to another disk.

Thanks for the help in advance.

---

### Post by StuartN on 2009-10-20
> **photon5 said:**
> While in /lib I accidentally chmod the cpp link.

On my system that is a link to /etc/alternatives/cpp

---

### Post by sisco311 on 2009-10-20
try:
```
sudo update-alternative --auto cpp
sudo update-alternative --auto cpp
sudo apt-get install --reinstall cpp-4.1
```

or:
```
sudo ln -s -T /etc/alternatives/cpp /lib/cpp
sudo chmod 0755 /lib/cpp
```

/lib/cpp is a symbolic link to /etc/alternatives/cpp
/etc/alternatives/cpp is a link to /usr/bin/cpp
/usr/bin/cpp is a link to /usr/bin/cpp-<version no.>
:)

---

### Post by photon5 on 2009-10-20
Thanks for the help everyone.  When I logged into the system with my system rescue cd and mounted the partitions, the cpp links seemed liked they were in place with the right permissions.  However, when I rebooted I still got stuck on /sbin/init.d permission denied.  I logged back in with the live cd and permissions seemed fine on /sbin/init.d.

At this point I thought I would replicate what I did that got me in the whole mess.  I chmod 755 /*/*.  I originally wanted to do that for a music directory but not really meaning to start with '/' Then I went and refixed the sudo doers file.

I'm up and running again.  I'll need to go and fix permissions but at least it's running.  I'll be a little more careful this time.  Good thing this server isn't open to the world.

Any ideas on getting the permissions right?

---

