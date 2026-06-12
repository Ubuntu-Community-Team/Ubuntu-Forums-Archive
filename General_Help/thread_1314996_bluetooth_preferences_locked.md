---
title: "bluetooth preferences locked?"
date: 2009-11-04
forum: General Help
---

### Post by PlancksCnst on 2009-11-04
I'm having trouble with bluetooth preferences. I can get the program open by clicking on the bluetooth applet in the notification area or by gong through the system menu. Once it's open, I can't change anything - it's all locked. It doesn't ask me for a password or anything - it just doesn't let me do anything. How can I modify the settings?

---

### Post by PlancksCnst on 2009-11-07
I'm surprised I haven't gotten any replies here. I still can't change any Bluetooth preferences.

---

### Post by ethos101 on 2009-11-20
BUMP.  Same here.

I had initially set up a USB dongle and paired it with my phone.  Then I installed Blueman, then discovered Blueman isn't compatible and uninstalled Blueman.  Now my Bluetooth Preferences is all greyed out and I can't do anything.  No matter how many times I reboot or unplug and plug in the USB dongle.  I turned bluetooth off on my phone and it's still litsted in that greyed out box.

Anybody here familiar with bluetooth?

---

### Post by kridybel on 2009-12-26
same issue

please help

---

### Post by walmis on 2009-12-26
> **ethos101 said:**
> BUMP.  Same here.

I had initially set up a USB dongle and paired it with my phone.  Then I installed Blueman, then discovered Blueman isn't compatible and uninstalled Blueman.  Now my Bluetooth Preferences is all greyed out and I can't do anything.  No matter how many times I reboot or unplug and plug in the USB dongle.  I turned bluetooth off on my phone and it's still litsted in that greyed out box.

Anybody here familiar with bluetooth?

Why do you think blueman isn't compatible? It works fine in ubuntu 9.10. 
Maybe there's problem with your adapter?
Is it listed in hciconfig?

---

### Post by kridybel on 2009-12-27
First of all thanks for the follow up.

I am having the same experience as ethos. Bluetooth worked first time with blueman. Then I removed blueman because I saw two bluetoot icons. After that bluetooth preferences stays greyed out. A screenshot is attached.

Here are some more details.

the output from lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 005 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

There is a  hciconfig file in the directory usr/sbin. I cannot open this file. sudo gedit gives a message "cannot open ... possibly a binary file"

There is also a hciconfig.8.gz file in the usr/share/man/man8 directory. This archive holds a hciconfig.8 file. I have attached this file to this post.

Hope you can help me further.

---

### Post by walmis on 2009-12-27
> **kridybel said:**
> First of all thanks for the follow up.

I am having the same experience as ethos. Bluetooth worked first time with blueman. Then I removed blueman because I saw two bluetoot icons. After that bluetooth preferences stays greyed out. A screenshot is attached.

Here are some more details.

the output from lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 005 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

There is a  hciconfig file in the directory usr/sbin. I cannot open this file. sudo gedit gives a message "cannot open ... possibly a binary file"

There is also a hciconfig.8.gz file in the usr/share/man/man8 directory. This archive holds a hciconfig.8 file. I have attached this file to this post.

Hope you can help me further.

:)

You need to run hciconfig, not open it in a text editor.
Open up accessories -> terminal
and enter:
*hciconfig*
and 
*rfkill list*

and copy-paste the output here.

---

### Post by kridybel on 2009-12-27
here is the output from the commands:
```
kris@kris-desktop:~$ hciconfig
hci0:	Type: USB
	BD Address: 00:11:67:D6:AE:E1 ACL MTU: 1021:4 SCO MTU: 48:10
	DOWN 
	RX bytes:684 acl:0 sco:0 events:21 errors:0
	TX bytes:88 acl:0 sco:0 commands:23 errors:1

kris@kris-desktop:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
kris@kris-desktop:~$ 

```

---

### Post by walmis on 2009-12-27
try
*sudo hciconfig hci0 up*
that should bring up the adapter.

---

### Post by kridybel on 2009-12-27
thx for follow up, But still no success:

```
kris@kris-desktop:~$ sudo hciconfig hci0 up
[sudo] password for kris: 
Can't init device hci0: Connection timed out (110)
kris@kris-desktop:~$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)

```

---

### Post by walmis on 2009-12-27
Well, i can say that this adapter is poorly supported. Those timeout errors usually mean there's a problem with the driver or the adapter itself.

---

### Post by kridybel on 2009-12-27
the strange thing is thow that it actually worked before I removed blueman.

---

### Post by kridybel on 2009-12-29
The solution that worked for me is based on this post:
[http://http://ubuntuforums.org/showthread.php?t=224673&page=8]("http://http://ubuntuforums.org/showthread.php?t=224673&page=8")

What I actually did was:

1. reinstalled blueman

2. added a few lines of code to **/etc/init.d/bluetooth**

Insert this BEFORE exit 0 at the end of the script:

```

sleep 1 && /usr/sbin/hciconfig hci0 reset
sleep 1 && /usr/sbin/hciconfig hci0 reset
```


3. remove everything in the   /var/lib/bluetooth/ directory

4. Restarted pc.

Then everything worked back normal.

---

