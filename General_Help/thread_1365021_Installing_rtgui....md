---
title: "Installing rtgui..."
date: 2009-12-26
forum: General Help
---

### Post by rwt911 on 2009-12-26
I am using [their]("http://code.google.com/p/rtgui/wiki/ubuntu_rtgui") guide to installing it but  when I get to the 6th step and restart apache I get thus error

```
rwt@rwt-laptop:~$ sudo apache2ctl restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```Can anyone help?

Thanks

---

### Post by rwt911 on 2009-12-26
Sorry, bumping this :)

---

### Post by jonest1 on 2009-12-26
I've gotten this error when setting up Apache before as well.  Google has a lot of information on the subject.

For starters, check to see if Apache is running.

sudo /etc/init.d/apache2 status

If not, try to start and check again.  Also, run 'netstat -an | grep LISTEN' and see if port 80 is listening (or whatever port you have configured.

If the server is just going to running locally, try to have the ip address fqdn in the /etc/hosts file.  If on a LAN, try to have your DNS server configured with the hostname, etc. 

There are other fixes and checks for this as well.  Google is your friend on this one.

---

