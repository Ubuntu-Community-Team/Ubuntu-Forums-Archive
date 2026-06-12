---
title: "I can load on runlevels my commands."
date: 2010-08-11
forum: General Help
---

### Post by wertum on 2010-08-11
I can load on runlevel 2 3 4 5 this command :
sudo -s user VBoxManage startvm debian --type headless

and on 0 1 6 runlevels a can load this command :
VBoxManage controlvm debian savestate .

I do:
1. Create file /etc/init.d/vbox_guest :> #! /bin/sh
### BEGIN INIT INFO
# Provides: vbox_guest
# Required-Start: $remote_fs $syslog $all
# Required-Stop: $remote_fs $syslog $all
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Example initscript
### END INIT INFO

PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

#

do_start() {
log_begin_msg "Run VirtualBox_Guest"
sudo -u user VBoxManage startvm debian --type headless
}

do_stop() {
log_begin_msg "Stop VirtualBox_Guest"
sudo -u user VBoxManage controlvm debian savestate
}

case "$1" in
start)
do_start
;;
restart|reload|force-reload)
echo "Error: argument '$1' not supported" >&2
exit 3
;;
stop)
do_stop
;;
*)
echo "Usage: $0 start|stop" >&2
exit 3
;;
esac2. Enter command:
chmod +x /etc/init.d/vbox_guest

3.Enter this command:
update-rc.d vbox_guest defaults 99

End.


OOPS! my VirtualBox Virtual Machine is not started after reboot.

:-( 

Please help me.

---

