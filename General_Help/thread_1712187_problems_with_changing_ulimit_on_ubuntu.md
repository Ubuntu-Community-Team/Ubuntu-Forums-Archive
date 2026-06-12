---
title: "problems with changing ulimit on ubuntu"
date: 2011-03-22
forum: General Help
---

### Post by dhanashreesathe on 2011-03-22
Have installed Ubuntu 10.0.4 on VMWare workstation. I wanted to change the number of open files, so I needed to change the /etc/security/limits.conf file. I updated the file and added the entries 
 
* hard nofile 20480
* soft nofile 20480
 
However, when I reboot I still see no of open files as 1024 after doing a ulimit -a as the root user.
 
I also added the line - session required pam_limits.so to /etc/pam.d/common-session.
 
Please let me know if anyone has faced a similar problem and resolved the issue.[B]


[/B]

---

