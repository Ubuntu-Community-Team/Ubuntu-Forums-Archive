---
title: "Ubuntu with Xen: &quot;address space collision&quot;"
date: 2011-05-24
forum: General Help
---

### Post by Rui Esteves on 2011-05-24
Hi,
I am trying to install Xen on Ubuntu, and I am using the documentation on [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen).
I installed Ubuntu Lucid 10.04 LTS and Xen 4.0.1
The kernel that I got is 2.6.32.40 (so i replace everywhere in the instructions the 2.6.32.32 by 2.6.32.40)

After editing file /etc/xen/xend-config.sxp, I reboot and get an error "address space collision".
I believe that something might be wrong when editing that file. The instructions say to comment out (xend-unix-server yes). However the file did not have that line but had the line (xend-unix-server no) commented. And I took out the comment of this line.

Any idea on how should I set-up this configuration file?

Thank you
[FONT=monospace]Rui[/FONT]

---

