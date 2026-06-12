---
title: "Ubuntu 10.4 startup scripts not working??"
date: 2010-08-09
forum: General Help
---

### Post by damang111 on 2010-08-09
Hello,
I downloaded Lucid and installed Mysql and Apache2.
I am very familiar with this setup and don't see a reason why this should not work.
apache2 and mysql scripts are already located in /etc/init.d
chkconfig shows the following:
apache2                     on
mysql                       2345

ps -aux does not show these processes running after a reboot.

the services start manually without any problems.
there is nothing in the logs that shows it's even trying to startup at boot.
What has changed in the new Ubuntu version?

I need this fixed through command line only.

thanks.

---

### Post by damang111 on 2010-08-09
Just figured out the problem was the loopback interfaces were not setup on my system.
adding: 

auto lo
iface lo inet loopback

to interfaces fixed the problem.

---

### Post by DaveLevy on 2010-08-21
I am tracking down a similar problem about startup scripts not working. This seems not to be a thread on startup scripts. i.e. it seems poorly titled.

---

