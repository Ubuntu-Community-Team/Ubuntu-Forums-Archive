---
title: "upstart vs sysv"
date: 2010-09-18
forum: General Help
---

### Post by Athunye on 2010-09-18
What is the correct way to stop upstart services from staring at boot time ?


I'm doing something like this example in /etc/init/mysql.conf:
```

#start on (net-device-up
#          and local-filesystems
#	  and runlevel [2345])
start on runlevel [!0123456] # I ADDED THIS LINE (and commented the above ones)
stop on runlevel [016]
```

1. Is this the correct way ?
2. Is there no way of doing something like we do with *update-rc.d -f apache2 remove* ?
3. When will ubuntu ship a gui to add or remove services from boot ?

---

### Post by bodhi.zazen on 2010-09-18
> **Athunye said:**
> What is the correct way to stop upstart services from staring at boot time ?


I'm doing something like this example in /etc/init/mysql.conf:
```

#start on (net-device-up
#          and local-filesystems
#      and runlevel [2345])
start on runlevel [!0123456] # I ADDED THIS LINE (and commented the above ones)
stop on runlevel [016]
```1. Is this the correct way ?
2. Is there no way of doing something like we do with *update-rc.d -f apache2 remove* ?
3. When will ubuntu ship a gui to add or remove services from boot ?

You could edit the init script in several ways, nothing wrong with your method.

+1 it would be nice if there were some tools to manage these things, command line or graphical.

File a bug against upstart on LP , make the suggestion for such tools, see what kind of a response you get.

---

