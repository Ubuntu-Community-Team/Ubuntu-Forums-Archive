---
title: "display services on command line"
date: 2009-10-24
forum: General Help
---

### Post by slooow on 2009-10-24
Hi, 

Is there a command line utility to display running services or find out if there are stopped?

My linux experience orginates from Gentoo. One utility I miss dearly is 'rc-status' which displays all installed services and if they are running, stopped or starting. The question has already been asked and the solution is usually 'rcconf' or 'ps'.

Rcconf displays the running services alright. However it does not display all the services, for example syslog is not displayed or if a service has not started for some reason, you cannot figure that out. With 'ps' you can find out if a service is running but it is not possible as far as I know to filter for services.

Is there another solution?

---

### Post by cilynx on 2009-10-25
'top' and 'ps waux' are the old-school way --

---

### Post by person7 on 2009-10-29
Hello !
 
in REDHAT distros i remember that there was a command "ntsysv" similar to "rcconf",
but it would display ALL services and their status. You can enable or disable services via "ntsysv" from the command line.
 
I'm also searching for a command like "ntsysv" in ubuntu 9.04
 
Any ideas?
 
Thank you for your help in advance!

---

### Post by krige on 2010-04-02
An equivalent to "ntsysv" in Ubuntu could be "sysv-rc-conf".

---

### Post by stans on 2010-04-02
I've been looking for 'services' and am surprised that it doesn't exist here.

---

