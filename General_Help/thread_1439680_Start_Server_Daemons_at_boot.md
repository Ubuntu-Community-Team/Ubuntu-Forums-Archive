---
title: "Start Server Daemons at boot"
date: 2010-03-26
forum: General Help
---

### Post by imahussey on 2010-03-26
Hi all, I recently set up a LAMP server in 9.10 non-server edition as I wanted a GUI. I'm looking for the correct way to start up these server daemons/services/processes during boot. I don't want to have to log into the server and run all the init commands. This has taken me on a journey the last two days and I'm a little frustrated to say the least. I come from a Fedora back ground to Ubuntu so I was used to chkconfig, and I tried to use a similar program sysv-rc-conf to no avail. 
Here are the commands I have to run each time the server reboots.
```
/etc/init.d/apache2 start
/etc/init.d/mysql start
/etc/init.d/ssh start
```

Also when I run sysv-rc-conf I show service levels 2,3,4,5 all ticked, and when I check my /etc/rc*.d directories I see each of the links labeled as they should be. S for 2,3,4,5 and K's for 0,1,S

---

