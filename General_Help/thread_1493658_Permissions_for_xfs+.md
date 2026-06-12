---
title: "Permissions for xfs+"
date: 2010-05-26
forum: General Help
---

### Post by waer01 on 2010-05-26
Hello,

  I've connected mac HDD through usb adapter. It mounts once ubuntu 10.04 is started and I can access it except these folders where you can see a white cross which are the most important to me:
[http://i50.tinypic.com/f5dfz4.png](http://i50.tinypic.com/f5dfz4.png)

I've opened mountmanager and tried to change something but it didnt help. It says something about permissions. here's an info that shows about hfs drive :

[http://img375.imageshack.us/f/img375/7302/screenshotmountmanager0.png](http://img375.imageshack.us/f/img375/7302/screenshotmountmanager0.png)

How should I access and copy those files ?

---

### Post by waer01 on 2010-05-26
thanks, found the solution already. mc commander with root access can enter those. Btw does anyone know a good, easy manual about mount command ?

---

### Post by srs5694 on 2010-05-26
Don't use root access for routine operations like this. You should instead adjust the permissions on the affected directories and/or change your user IDs (UIDs) under Mac OS X and/or Linux to match each other.

A Web search turns up several tutorials on these topics:

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html)
[http://www.linuxhelp.net/newbies/#chown](http://www.linuxhelp.net/newbies/#chown)
[http://code.google.com/edu/tools101/linux/ownership_permissions.html](http://code.google.com/edu/tools101/linux/ownership_permissions.html)

---

