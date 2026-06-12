---
title: "dbus not get started by upstart"
date: 2012-04-26
forum: General Help
---

### Post by h113331pp on 2012-04-26
Let me apologize for my poor English, I`m not a native speaker.

I`m using 12.04 in my intel n2800 target board, and got a problem that the dbus not runing.

I checked the /etc/init/dbus.conf:

/******************************dbus.conf**************************************/
# dbus - D-Bus system message bus
#
# The D-Bus system message bus allows system daemons and user applications
# to communicate.

description     "D-Bus system message bus"

start on local-filesystems
stop on deconfiguring-networking

expect fork
respawn

pre-start script
    mkdir -p /var/run/dbus
    chown messagebus:messagebus /var/run/dbus

    exec dbus-uuidgen --ensure
end script

exec dbus-daemon --system --fork --activation=upstart

post-start exec kill -USR1 1

post-stop exec rm -f /var/run/dbus/pid
/***********************************************************************************************/

it`s looks like dbus will run after I get my file system working.

but it`s not working until I create a file named /etc/rc2.d/S12dbus,

and the following is the content:

/etc/init.d/dbus start 

Could someone please tell me why?

---

