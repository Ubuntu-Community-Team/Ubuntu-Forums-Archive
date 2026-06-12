---
title: "how to know webserver user id"
date: 2006-05-04
forum: General Help
---

### Post by jeisma on 2006-05-04
hi!

im trying to install an application, somewhere along the guide, i came across that says something like this:

"The "var" folder in the root installation MUST be able to be written to by your web server"

i guess it means the webserver must have read/write access to the folder. how do i know if the webserver has this privileges on the folder? how do i know the user id of the web server?

thanks!

---

### Post by chris_andrew on 2006-05-04
I guess the UID should be in /etc/passwd.

---

### Post by paul.maddox on 2006-05-04
Depends on the web server really.

I know for apache the user it runs as is stored in the apache configuration file.

For example on one of my apache 1.3.34 webservers it has the following in the httpd.conf file:

```
# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.
#
# User/Group: The name (or #number) of the user/group to run httpd as.
#  . On SCO (ODT 3) use "User nouser" and "Group nogroup".
#  . On HPUX you may not be able to use shared memory as nobody, and the
#    suggested workaround is to create a user www and use that user.
#  NOTE that some kernels refuse to setgid(Group) or semctl(IPC_SET)
#  when the value of (unsigned)Group is above 60000;
#  don't use Group "#-1" on these systems!
#
User apache
Group admin

```

Hope this helps.

---

