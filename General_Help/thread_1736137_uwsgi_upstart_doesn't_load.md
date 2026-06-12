---
title: "uwsgi upstart doesn't load?"
date: 2011-04-22
forum: General Help
---

### Post by Pawhi on 2011-04-22
Dear Ubuntu Community members,

I'm trying to setup an nginx server with uwsgi. For this i want to start uwsgi with an upstart in /etc/init/.

My upstart file, named "uwsgi.conf", looks like this:
```
# /etc/init/uwsgi.conf
description "uwsgi server"
start on runlevel [2345]
stop on runlevel [!2345]
respawn
exec /etc/uwsgi \
--processes 2 \
--home /var/www/ngtest/djangoapp/ \
--socket /var/run/uwsgi.sock \
--chmod-socket \
--module wsgi \
--pythonpath /var/www/djangoapp
--daemonize /var/log/uwsgi.log
# home - is the path to our virtualenv directory
# module - is the file name of our wsgi configuration
# pythonpath is the path to our django application
# socket specifies the UNIX socket file to use.

```But after restarting the server or typing "initctl reload-configuration" uwsgi is still not started or controllable. Are you seeing any problem with this file? Maybe a Problem with the execute path?

Thanks and greetings,

Pawhi

---

### Post by ajaxaddicted on 2011-05-06
Hi Pawhi,

It took me some time to find this, but Upstart doesn't trigger any errors. You can find what you are looking for in your syslog file. So

start uwsgi

And after that check /var/log/syslog

---

