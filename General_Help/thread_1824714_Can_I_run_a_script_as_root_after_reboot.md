---
title: "Can I run a script as root after reboot?"
date: 2011-08-14
forum: General Help
---

### Post by Kissell on 2011-08-14
Everytime I reboot Ubuntu, I have to run a sudo command.  The vmware virtual network card is only accessible by root.  I need normal users to be able to use it, after giving it proper permissions with chmod everybody is happy, until I reboot, then the device is recreated/reset to only root having access to it.  

After reboot:
```
ls -l /dev|grep vm
```
> 
crw-rw-rw-  1 root   root     10,  56 2011-08-14 06:06 vmci
crw-------  1 root   root     10, 165 2011-08-14 06:06 vmmon
crw-------  1 root   root    119,   0 2011-08-14 06:06 vmnet0
crw-------  1 root   root    119,   1 2011-08-14 06:06 vmnet1
crw-------  1 root   root    119,   8 2011-08-14 06:06 vmnet8


I fix it:
```
sudo chmod a+rw /dev/vmnet0
```

After I fix it:
```
ls -l /dev|grep vm
```
> 
crw-rw-rw-  1 root   root     10,  56 2011-08-14 06:06 vmci
crw-------  1 root   root     10, 165 2011-08-14 06:06 vmmon
crw-rw-rw-  1 root   root    119,   0 2011-08-14 06:06 vmnet0
crw-------  1 root   root    119,   1 2011-08-14 06:06 vmnet1
crw-------  1 root   root    119,   8 2011-08-14 06:06 vmnet8


I need to be able to script that command somehow...  however, it needs to be a sudo command, and I don't want to have to enter the root password after a reboot.  I need anyone to be able to pull the plug on the server and turn it back on and for it to work without my interaction everytime it is rebooted.

Surely that's possible, right?

---

### Post by raja.genupula on 2011-08-14
we need root or his password . you said its have sudo . so when ever this script executing i think it should need root password.i am saying under my knowledge .

---

### Post by haqking on 2011-08-14
> **raja.genupula said:**
> we need root or his password . you said its have sudo . so when ever this script executing i think it should need root password.i am saying under my knowledge .

you dont need root, root is disabled by default in ubuntu and should stay that way.

Sudo is used to perform admin tasks.

you can script it with sudo priveleges and see here for shutdown/startup scripts

[http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown](http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown)

---

### Post by Kissell on 2011-08-14
I was trying to use "cron" to run it with root privledges.

but this entry surprisingly didn't work...  it must run it before it shutsdown, or upon reboot before that device is created.
"@reboot chmod a+rw /dev/vmnet0"

---

### Post by Kissell on 2011-08-14
> **haqking said:**
> 
you can script it with sudo priveleges and see here for shutdown/startup scripts

[http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown](http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown)

okay, cool, I put some commands in /etc/rc.local and they seem to be running at startup even though they normally need me to run them with sudo.  you're 2 for 2.

---

### Post by haqking on 2011-08-14
> **Kissell said:**
> okay, cool, I put some commands in /etc/rc.local and they seem to be running at startup even though they normally need me to run them with sudo.  you're 2 for 2.

no problem glad could help.

remember to mark thread as solved from thread tools to aid other people when solving a problem

---

