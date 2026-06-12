---
title: "dansguardian will not start"
date: 2010-04-04
forum: General Help
---

### Post by capnjim on 2010-04-04
I have installed dansguardian on Kubuntu Karmic. Dansguardian is not starting at boot. When I try and manually start the service I get:

> 
sudo service dansguardian start
 * Starting DansGuardian dansguardian                                                                                                                                                                                                       Error creating/opening pid file:/var/run/dansguardian/dansguardian.pid
Exiting with error


If I then manually create /var/run/dansguardian with "sudo mkdir /var/run/dansguardian" the service will then launch happily. Of course, after reboot /var/run/dansguardian is removed and I am back at sqaure one.

I would greatly appreciate some guidance on what I can do to get this working at boot.

---

