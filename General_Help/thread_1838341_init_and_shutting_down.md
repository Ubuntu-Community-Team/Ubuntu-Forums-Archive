---
title: "init and shutting down"
date: 2011-09-03
forum: General Help
---

### Post by bonfire89 on 2011-09-03
Short Question: does (essentially) "/etc/ini.d/* stop" run when shutting down?

Full Question:

I'm about to implement a script very similar to 

```
#! /bin/sh
# /etc/init.d/SpodeVM
#

#Edit these variables!
VMUSER=spode
VMNAME="My VM Name"

case "$1" in
  start)
    echo "Starting VirtualBox VM..."
    sudo -H -b -u $VMUSER /usr/bin/VBoxVRDP -s "$VMNAME"
    ;;
  stop)
    echo "Saving state of Virtualbox VM..."
    sudo -H -u  $VMUSER /usr/bin/VBoxManage controlvm "$VMNAME" savestate
    ;;
  *)
    echo "Usage: /etc/init.d/SpodeVM {start|stop}"
    exit 1
    ;;
esac

exit 0
```
source: [http://www.spodesabode.com/discussion/310/virtualbox-vm-on-boot-with-ubuntu/](http://www.spodesabode.com/discussion/310/virtualbox-vm-on-boot-with-ubuntu/)

It is important that the virtualbox shuts down properly when I shutdown the host, will "/etc/init.d/SpodeVM stop" run when I "shutdown -r now" or "init 0" ?


Thanks

---

### Post by bonfire89 on 2011-09-03
man update-rc.d 

> Kill scripts are called first, passing a stop argument.


the answer to my question appears to be "yes"

solved

---

