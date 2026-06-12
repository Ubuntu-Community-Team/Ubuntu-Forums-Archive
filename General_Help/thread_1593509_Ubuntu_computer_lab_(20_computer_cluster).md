---
title: "Ubuntu computer lab (20 computer cluster)"
date: 2010-10-11
forum: General Help
---

### Post by karaluch on 2010-10-11
I'm a BSD guy, so i'm new to Linux. I've been asked to fix a computer lab with 20 computers. They need to be operational soon so i don't really have time to study all the documentation, so i kindly ask for help. The installations are in a pretty bad shape, so i will reinstall them with the newest version of Ubuntu. User authentication is via LDAP, user homes are mounted with NFS using autofs. I'll use the simplest form of installing and managing the computers: install on one, rsync to others from the livecd, manage with clusterssh. There are some problems i don't know how to fix:
-make gdm LDAP-friendly -- don't do any caching, any automounting, any "login frequency" logging etc
-remove all the graphical network configurators, packet upgraders, automatic package updates and similar desktop/laptop features
-allow regular users to mount cdroms and pendrives
-disk UUIDs seem to be identical on all machines, but not udev network interfaces, perhaps a wildcard '*' in ADDR in the udev configuration files will do? Or perhaps i should disable udev completely? (how?) I want the computers to be as similar as possible.
What directories can i expect to differ on all the machines, apart from /var and /tmp?

I ask for any suggestions, thanks in advance. Also please post any additional tips.

---

