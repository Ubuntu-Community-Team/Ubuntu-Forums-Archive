---
title: "Remote Desktop Problem"
date: 2010-10-15
forum: General Help
---

### Post by wisie on 2010-10-15
I recently upgraded Ubuntu 10.10 and had a screen [issue]("http://ubuntuforums.org/showthread.php?p=9964175#post9964175"). I think this might have caused problems with my vnc remote access to the machine.  Trying to connect to the machine, my connection is rejected. Upon plugging a screen into the box, the remote desktop settings are still setup within Ubuntu so it seems strange I can't connect to the machine.

I don't suppose anyone has any suggestions to what could be wrong and not letting me connect to the machine via VNC? I can still SSH fine, it's just the VNC that doesn't seem to want to work.

Thanks and I appreciate any help :)

---

### Post by luvshines on 2010-10-15
Is the machine from which you are trying to connect to Windows or Linux ??

Check if port 5900 of the server is reachable or not. If you are trying from Linux box:
```
nc -zv <server-ip> 5900
```

I don't know the equivalent Windows command :(

If it is not reachable, check the same on the server itself.
Also make sure not firewall rules on the server are blocking that port
```
sudo iptables -L
sudo ufw status
```

---

### Post by wisie on 2010-10-15
Sorry should have added that.

My machine (Windows 7) is trying to connect to a Ubuntu 10.10 desktop version.

No firewalls are turned on my router or either computers.

```
alex@server:~$ nc -zv server 5900
nc: connect to server port 5900 (tcp) failed: Connection refused
nc: connect to server port 5900 (tcp) failed: Connection refused
nc: connect to server port 5900 (tcp) failed: Connection refused

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Strange :S

---

### Post by luvshines on 2010-10-15
See if Comment #21 helps you:
[http://ubuntuforums.org/showthread.php?t=1593398&page=3](http://ubuntuforums.org/showthread.php?t=1593398&page=3)

Basically, uncheck everything and close the Remote Desktop setting box.
**Then reopen it and check everything you want to but leave 'Configure network automatically ...' box.**

Also you might want to check this on the server:
```
netstat -an | grep 5900
```

---

### Post by annoyingrob on 2010-10-15
So it worked before you upgraded, and doesn't now?

Sounds kind of silly, but is your VNC server running on bootup?

---

### Post by wisie on 2010-10-15
> **luvshines said:**
> See if Comment #21 helps you:
[http://ubuntuforums.org/showthread.php?t=1593398&page=3](http://ubuntuforums.org/showthread.php?t=1593398&page=3)

Basically, uncheck everything and close the Remote Desktop setting box.
**Then reopen it and check everything you want to but leave 'Configure network automatically ...' box.**

Also you might want to check this on the server:
```
netstat -an | grep 5900
```

Thanks! I will look into that thread :)

> **annoyingrob said:**
> So it worked before you upgraded, and doesn't now?

Sounds kind of silly, but is your VNC server running on bootup?

Yup. Very strange.

---

### Post by wisie on 2010-10-17
> **luvshines said:**
> See if Comment #21 helps you:
[http://ubuntuforums.org/showthread.php?t=1593398&page=3](http://ubuntuforums.org/showthread.php?t=1593398&page=3)

Basically, uncheck everything and close the Remote Desktop setting box.
**Then reopen it and check everything you want to but leave 'Configure network automatically ...' box.**


This fixed things perfectly. Thank you!

---

