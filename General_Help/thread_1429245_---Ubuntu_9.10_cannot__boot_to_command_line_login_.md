---
title: "---Ubuntu 9.10 cannot  boot to command line login screen"
date: 2010-03-13
forum: General Help
---

### Post by bzhao on 2010-03-13
Dear all,

  I have used the below command to do that successfully for the previous version of ububunt, but this time I failed to do that with Ubuntu 9.10. Why? Please help!

  I know I can do that manually by "sudo /etc/init.d/gdm stop" command.
  I try to change the name of /etc/init.d/gdm files, but the problem still exist.

"sudo update-rc.d -f gdm remove"

Thanks in advance.

Bill Z

---

### Post by Brandon Williams on 2010-03-16
Use sudo to open the file /etc/X11/default-display-manager and remove all of its contents. If that file is empty, upstart will no longer start gdm.

---

### Post by bzhao on 2010-03-19
Thanks for your answer. it works.

---

### Post by bzhao on 2010-04-10
I find out a method&#65306;
add :2" at the 13rd line  in /etc/init/gdm.conf 
as "stop on runlevel [0216]"

The old method("sudo update-rc.d -f gdm remove") works untill 9.04, but this mehtod work at 9.10

---

