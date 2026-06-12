---
title: "DHCP server is not starting in startup"
date: 2009-08-05
forum: General Help
---

### Post by zajith on 2009-08-05
How to configure DHCP server to start in Boot. 

I have configured DHCP server and it is working fine if I give the command
/etc/init.d/dhcp3-server start

but after every reboot I have to give this command manually ,please provide the information to start DHCP server automatically while booting

Thanks in advance

---

### Post by soapBAR2 on 2009-08-05
The simple solution would be to add a script to your Autostart menu. If you use KDE, this is

```
nano ~/.kde/Autostart/scriptname
>> #!/bin/bash
>> /etc/init.d/dhcp3-server start
sudo chmod +r ~/.kde/Autostart/scriptname

```

Don't know about other DM/DEs, sorry, but most have something in a settings menu somewhere.

The other possibility is that your network manager (which is just a frontend to /etc/network/interfaces ) either does not have "auto interfacename" line in it, or it is not set to dhcp. (The relevant parts of) my /etc/network/interfaces look like this;

```
auto eth0
iface eth0 inet dhcp

```

Make sure you have both lines, the only thing that should be different is eth0 (and even then it probably won't be different). Be careful when editing your /etc/network/interfaces, make a backup if you're new to it (like this)

```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

and if it all goes to hell,

```
sudo cp /etc/network/interfaces.backup /etc/network/interfaces
```

Check the man page (man interfaces) for more details.

PS. Your network manager may or may not complain about you editing your interfaces file. For example, if you're using wicd, it sets the mode to "manual", and breaks if you change it. YMMV

---

### Post by shaferwr on 2010-04-19
I have the same problem as the original poster.
 
I'm running dhcp3-server and everything works perfectly... until I reboot. 
 
I have to manually start the dchp3-server with /etc/init.d/dhcp3-server start
 
Any help would be greatly appreciated.
 
Edit:  I found the fix thanks to phil123:
[http://ubuntuforums.org/showthread.php?p=9144235#post9144235](http://ubuntuforums.org/showthread.php?p=9144235#post9144235)

---

