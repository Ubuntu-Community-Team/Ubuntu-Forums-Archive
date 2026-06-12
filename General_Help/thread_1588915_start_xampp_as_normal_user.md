---
title: "start xampp as normal user"
date: 2010-10-05
forum: General Help
---

### Post by jodlajodla on 2010-10-05
hello!
is there any way to start xampp as normal user and not root. 

Thank you! :)

---

### Post by XeonBloomfield on 2010-10-05
If the root install the package fakeroot - of course !
Then it is very simple:
"fakeroot <your command>".

Maybe there are other options, but I`m not working with xampp.

---

### Post by jodlajodla on 2010-10-06
Thanks!

Is there any other option, for start xampp?

---

### Post by jodlajodla on 2010-10-09
> **XeonBloomfield said:**
> If the root install the package fakeroot - of course !
Then it is very simple:
"fakeroot <your command>".

Maybe there are other options, but I`m not working with xampp.

I've tried this, but I just got many errors and XAMPP haven't work ;)

Please, I really need XAMPP.

Thanks!! :)

---

### Post by XeonBloomfield on 2010-10-09
I do not know how to run differently than written.

I tried to run it on my PC and displays:

```
xeon@xeon-desktop:~$ /opt/lampp/lampp start
You need to start XAMPP as root!
xeon@xeon-desktop:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
xeon@xeon-desktop:~$ 

```

---

### Post by jodlajodla on 2010-10-09
I just type fakeroot, and then I start xampp. If I type only sudo /opt/... start, I get this: user is not in the sudoers file.  This incident will be reported. ;)

With fakeroot there is no option, because I get many errors. Is there any other "webserver" which will works without administrator rights?

Thanks! :)

---

### Post by XeonBloomfield on 2010-10-09
You can not install content xampp normally to run as when turning on the system?

There is a possibility that the file "/etc/rc.local" add "/opt/lampp/lampp start" line before "exit 0". (You must edit it as root, eg: "sudo gedit /etc/rc.local")

For a directory containing the access rights you give the command: 
"chown YOUR_USERNAME:users /opt/lampp/htdocs" 
and 
"chown YOUR_USERNAME:users /opt/lampp/cgi-bin".

---

### Post by Gunman1982 on 2010-10-09
Don't use fakeroot to start programm, it is not inteded for that, It's intended for purposes like packaging archives and stuff.

If you don't have root/sudoers rights you won't be able to run any webserver on a port lower than 1024 (default port the webserver listens on is 80). 

Never used xampp on Linux so can't help you much there but I'm pretty sure with probably a medium amount of afford you can run it as a user, still not on the default web server port though.

---

