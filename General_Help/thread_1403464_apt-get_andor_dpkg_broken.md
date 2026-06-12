---
title: "apt-get and/or dpkg broken"
date: 2010-02-10
forum: General Help
---

### Post by DustyMP on 2010-02-10
I installed a 8.04 server operating system on a machine and wanted to explore gbindadmin so I used apt-get to download and install ubuntu-desktop. After the downloads completed the packages began installing and the system crashed. When I rebooted the system started on tty1 again and I tried apt-get install again. I received and error directing me to run "dpkg --configure -a" and when I did that the install resumed again. However part way through error messages started flying after each package saying they could not be configured and the install aborted. I shut if of, walked away for a bit, and when I rebooted gnome's login screen came up. I tried logging in and it failed, and I can't switch to any other TTY. I can however get in using gnome's failsafe terminal. I tried dpkg --configure -a again and the failures start with saying /var/run/dbus does not exsist and cannot be configured. I tried (on a whim) dpkg --configure dbus and recieved:

```
setting up dbus (1.1.20-1ubuntu3.3) ...
Warning: The home dir /var/run/dbus you specified can't be accessed: No such file or directory
The user 'messagebus' already exsists. Exiting.
chown: cannot accesss '/var/run/dbus': No such file or directory
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dbus
kyle@ubuntuserver:$
```

Any suggestions what to try next?

---

### Post by sisco311 on 2010-02-10
/var/run/dbus is the home directory of the messagebus user, Try to create it & run dpkg --configure -a again:
```
mkdir /var/run/dbus
dpkg --configure -a

```

---

### Post by wojox on 2010-02-10
Why don't you just install the 8.04 Desktop edition?

---

### Post by DustyMP on 2010-02-10
sisco311, thank you very much, that has me moving again. Seems really obvious now.

wojox, I just didn't want to repeat all my work setting up my zones for bind and I don't have them saved yet. Reminds me of the addage "he who smiles after a crash has backups!"

---

