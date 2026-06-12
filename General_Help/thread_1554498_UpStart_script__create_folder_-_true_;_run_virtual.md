---
title: "UpStart script : create folder - true ; run virtualbox - false."
date: 2010-08-16
forum: General Help
---

### Post by wertum on 2010-08-16
script /usr/local/sbin/vbox_guest do_start()>  {
su -c 'VBoxManage startvm debian --type headless' user
su -c 'mkdir /home/what/sdfsdf' user
}

do_stop() {
su -c 'VBoxManage controlvm debian savestate' user
}

case "$1" in
start)
do_start
;;
stop)
do_stop
;;
*)
echo "Usage: $0 start|stop" >&2
exit 3
;;
esac I'm running on console (terminal) this command : telinit2 and this scipt create folder and don't running VirtualBox Virtual Machine.

How I do fix this problem?

---

