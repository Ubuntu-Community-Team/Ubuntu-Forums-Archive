---
title: "problem with upstart"
date: 2011-06-18
forum: General Help
---

### Post by Pawlerson on 2011-06-18
I installed mysql -server and it was started automatically from some reason. I use it just for testing and I want to have it disabled when system starts. I tried 'sudo service mysql disable', but it doesn't work:

> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql disable

The script you are attempting to invoke has been converted to an Upstart
job, but disable is not supported for Upstart jobs.

This error doesn't make any sense to me. I just want to start it when it's needed. With systemd it's very easy to do: 'systemctl disable mysql'. How am I supposed to do the same in Ubuntu?

---

