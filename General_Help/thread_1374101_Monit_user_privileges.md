---
title: "Monit user privileges"
date: 2010-01-06
forum: General Help
---

### Post by sedilson on 2010-01-06
Hi,
I'm using monit to restart vino-server in case of process fail.

I've created a script to check the vino-server pid and export to a vino.pid file.
So i've configured Monit to check this pid file.

So far so good.

What is happening is that I cannot start or stop the vino process using vino.
After some tests I've realized that if you use the start/stop with root privileges the command doesn't stop/start the vino process:

root@Server:~# gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
root@Server:~# gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false

But if I try it as a regular user it works:
administrador@Server:~$ gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
administrador@Server:~$ gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false

So I believe that Monit is trying to run this command with root privileges.

-> My dout in this case is: Is there a way to force Monit to run a command as user?

I've also tried:
su administrator -c gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

Doing that in command line a password is requested, but works. But including that in Monit config file doesn't, I belive because there is no way to type the password.

#
check process vino-server with pidfile /usr/lib/vino/PID/vino.pid
start program = "su adminstrador -c gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true"
stop program = "su adminstrador -c gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false"
#

Any suggestions?

Thanks a lot.

Edilson

---

### Post by iponeverything on 2010-01-06
upstart might be a better way to do it..

---

