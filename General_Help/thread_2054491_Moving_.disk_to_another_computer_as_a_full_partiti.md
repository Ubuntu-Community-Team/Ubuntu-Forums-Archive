---
title: "Moving .disk to another computer as a full partition"
date: 2012-09-07
forum: General Help
---

### Post by sammy0025 on 2012-09-07
Hi there,
I've been running a game server with Ubuntu 12.04 Precise, but as I noticed the amount of players increase, so do my need for better hardware increase. I want to know, if I buy a new computer and put Ubuntu 12.04 Precise on it, how can I move all of my files from my previous "game server" computer over? My "game server" computer is actually a Wubi installation on Windows 7 64-bit. I have adequate knowledge on systems with the bash shell, as well as file and SSH operations on the shell, and of course upgrading with apt-get. My question is that how should I get an entire root.disk (as a Wubi installation) to another computer running Ubuntu ONLY. 
Thanks in advance,
sammy0025

---

### Post by jerome1232 on 2012-09-07
Here is the Wubi Wiki to the rescue, it has some info about migrating wubi's virtual disk out to a real partition.

[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by sammy0025 on 2012-09-07
Thanks, but I've already looked into that idea of using a shell script to migrate it. The problem is that firstly, it is a separate computer, and secondly, I do not want the second computer to have Windows, as that will mean buying another license for it. My original plan was to install Windows and Wubi on the new computer, and copy over the root.disk. After that, I will go according to the MigrateWubi guide. Just to clarify another few things: is the GRUB bootloader considered to be present if I install Wubi, so I can specify the --no-bootloader option,and are 12.04s upgraded to 12.04.1s? I'm afraid that when I copy over that root.disk there could be incompatibilities, how do I create those partitions if I only have Windows and Wubi, and what should I do if I pre-install Ubuntu instead of Windows, and how should I do that? The guide's kinda confusing to be honest, or maybe because I'm not very good with disk management.

---

