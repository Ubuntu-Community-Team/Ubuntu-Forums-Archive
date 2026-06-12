---
title: "bluetooth disconnects after inactivity"
date: 2010-02-08
forum: General Help
---

### Post by hwttdz on 2010-02-08
My bluetooth devices disconnect after a period of inactivity (not sure exactly how long).  They're being connected with:

sudo hidd --connect

and I've made no edits to any bluetooth related system files so it should be default settings throughout.  I would like them to stay connected indefinitely, and it would be even better if they would stay connected through reboots.

---

### Post by hwttdz on 2010-02-10
Any suggestions?  Also is it possible to set the mouse/keyboard to connect on startup? 

I currently have a script to monitor for possible devices:
```
#!/bin/bash
while [ 1 ]
do

num_connected=`hidd --show|wc -l`;
if [ "2" == $num_connected ] ; then
#	echo -ne "two connected\n";
	sleep 5;
else
	echo "Scanning";
	hcitool scan|grep -E "mouse_addr|keyboard_addr"|grep -Ev "Scanning"|awk '{print $1}'|xargs -t -n 1 sudo hidd --connect;
fi
done
```

Pretty straightforward, if there are two devices connected stall for a bit.  Otherwise search for devices.  Of course I have to put the mouse and keyboard in discoverable mode every time I sit down (which is annoying), and it means there is a sort of "start up delay".

---

### Post by hwttdz on 2010-02-18
Any ideas?

---

### Post by datman on 2010-03-09
This is also driving me mad.... surely there must be a way?

---

### Post by Teracis on 2010-06-05
This would also solve my problem, trying to get the keyboard to work in a dual boot.

I can connect with sudo hidd --search, but as you say, this is not persistent after reboot.

---

