---
title: "db2admin failure on 11.04"
date: 2011-09-16
forum: General Help
---

### Post by kleach on 2011-09-16
The db2 express-c install, using sudo, on Ubuntu 11.04 leaves strange link behavior.
 
It looks like an issue with Ubuntu or the install requires real root and not sudo, but the resulting links in the das user home directory, das/bin, das/java, ... all give permissions errors.
 
The directory they link to is accessible, but the link gives an error.
 
I worked around this by renaming the installed liks to .bad and creating new links as the das user. All is well and I can now start the db2 control center...
 
Here are the final links:
 
#ls -ld ~dasusr1/das/* | grep '^l'
lrwxrwxrwx 1 dasusr1 dasadm1 25 2011-09-14 14:05 /home/dasusr1/das/bin -> /opt/ibm/db2/V9.7/das/bin
lrwxrwxrwx 1 root dasadm1 25 2011-09-14 13:59 /home/dasusr1/das/bin.bad -> /opt/ibm/db2/V9.7/das/bin
lrwxrwxrwx 1 dasusr1 dasadm1 26 2011-09-14 14:08 /home/dasusr1/das/conv -> /opt/ibm/db2/V9.7/das/conv
lrwxrwxrwx 1 root dasadm1 26 2011-09-13 09:20 /home/dasusr1/das/conv.bad -> /opt/ibm/db2/V9.7/das/conv
lrwxrwxrwx 1 dasusr1 dasadm1 30 2011-09-14 14:08 /home/dasusr1/das/function -> /opt/ibm/db2/V9.7/das/function
lrwxrwxrwx 1 root dasadm1 30 2011-09-13 09:20 /home/dasusr1/das/function.bad -> /opt/ibm/db2/V9.7/das/function
lrwxrwxrwx 1 dasusr1 dasadm1 26 2011-09-14 14:08 /home/dasusr1/das/java -> /opt/ibm/db2/V9.7/das/java
lrwxrwxrwx 1 root dasadm1 26 2011-09-13 09:20 /home/dasusr1/das/java.bad -> /opt/ibm/db2/V9.7/das/java
lrwxrwxrwx 1 dasusr1 dasadm1 25 2011-09-14 14:09 /home/dasusr1/das/lib -> /opt/ibm/db2/V9.7/das/lib
lrwxrwxrwx 1 root dasadm1 25 2011-09-13 09:20 /home/dasusr1/das/lib.bad -> /opt/ibm/db2/V9.7/das/lib
lrwxrwxrwx 1 dasusr1 dasadm1 25 2011-09-14 14:09 /home/dasusr1/das/msg -> /opt/ibm/db2/V9.7/das/msg
lrwxrwxrwx 1 root dasadm1 25 2011-09-13 09:20 /home/dasusr1/das/msg.bad -> /opt/ibm/db2/V9.7/das/msg
 
And here is the error, besides not being able to use the control center:
 
#cd /home/dasusr1/das/msg.bad
-bash: cd: /home/dasusr1/das/msg.bad: Permission denied
#cd /home/dasusr1/das/msg
#

---

