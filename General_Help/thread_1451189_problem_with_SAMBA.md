---
title: "problem with SAMBA"
date: 2010-04-10
forum: General Help
---

### Post by zeek333 on 2010-04-10
Hi 
I have kinda small problem with SAMBA server.

when I reboot my server it stops SAMBA: 

* nmbd is running
* could not access PID file for smbd

When i start manualy then is ok but after some it stop again with same error:

* nmbd is running
* could not access PID file for smbd

Ubuntu version 9.10 fresh install

P.S. smbd.conf

[global]

workgroup = WORKGROUP
server string = %h 
dns proxy = no
security = share
create mask = 0777
directory mask = 0777
security mask = 0777
directory security mask = 0777
   
#### Networking ####
bind interfaces only = yes
interfaces = eth1 192.168.1.1
    
#### Debugging/Accounting ####

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

#===== Share Definitions ==========

[Public]
comment = Public's share
path = /home/properties/Public
read only = no
public = yes
writable = yes
create mask = 0765

---

### Post by byStanderone on 2010-04-10
...have just been from this thread, a great tutorial on samba:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by zeek333 on 2010-04-10
Thanx for useful link 

I found my problem, it was interfaces = eth1 192.168.1.1 wrong 

should be only interfaces = eth1

---

