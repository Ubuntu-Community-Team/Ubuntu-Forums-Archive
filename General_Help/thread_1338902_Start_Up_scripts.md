---
title: "Start Up scripts"
date: 2009-11-26
forum: General Help
---

### Post by willie199120 on 2009-11-26
Hey there I am relatively new to Ubuntu and was wondering how to set up some terminal commands to be run on there own as I start up my computer.

First of all I want these set of commands to run:
```

sudo su -
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```

Which basically disables my ipv6
(this could be a good workaround to those with ipv6 bug errors on 9.04)

and then I would like to change my Mac by running this command:
```

sudo -i
ifconfig eth0 down hw ether 00:14:D1:C0:68:49

ifconfig eth0 up
ifconfig wlan0 down hw ether 00:14:D1:C0:68:49
ifconfig wlan0 up
```

How would I set up a script that would accomplish this? Where would  I place it? Please be detailed as I am still a new to Ubuntu.

---

### Post by dcstar on 2009-11-27
> **willie199120 said:**
> Hey there I am relatively new to Ubuntu and was wondering how to set up some terminal commands to be run on there own as I start up my computer.
.........
How would I set up a script that would accomplish this? Where would  I place it? Please be detailed as I am still a new to Ubuntu.

/etc/rc.local

---

### Post by raktarok on 2009-11-27
Look here if you want more details, otherwise just put the commands in the file /etc/rc.local as suggested above.You won't even need the lines to become root, as these files are read by the system during boottime as superuser.
[http://ubuntuforums.org/showthread.php?t=1338673](http://ubuntuforums.org/showthread.php?t=1338673)

---

### Post by willie199120 on 2009-11-27
EDit: Thanks alot guys

---

