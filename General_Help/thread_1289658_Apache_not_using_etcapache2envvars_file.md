---
title: "Apache not using /etc/apache2/envvars file"
date: 2009-10-12
forum: General Help
---

### Post by Zobeid on 2009-10-12
All my *nix experience up to now has been with Mac OS X, but a few days ago I subscribed to a Linode, initialized Ubuntu on it, and started moving all my server stuff to it.  After a bit of fumbling around, I got my basic stuff working -- including Apache.  However. . .

For some reason Apache isn't finding, or recognizing, or using the contents of /etc/apache2/envvars.  Mine looks like this:

```
# envvars - default environment variables for apache2ctl

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

```

This has resulted in some annoying errors -- including Apache creating a file named "${APACHE_PID_FILE}" if you can believe it.   :frown:

I'm not sure how /etc/apache2/envvars is supposed to be incorporated.  Is it supposed to be read by the shell before apache2 is started?  Is apache2 itself supposed to read it, and for some reason its failing to?

---

