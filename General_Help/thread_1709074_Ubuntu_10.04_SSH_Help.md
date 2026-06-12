---
title: "Ubuntu 10.04: SSH Help"
date: 2011-03-17
forum: General Help
---

### Post by SexySara on 2011-03-17
I changed my port to 1369 in the ect/sshd_config file and then restarted ssh by running the cmd in terminal...
```
/etc/init.d/ssh restart
```Now when I try to log in, mind you I am logging in to my box from the one I am on. I get an error from peer when trying to log in.
```
soultravel369@ANONYMOUS:~$ ssh -p 1369 soultravel369@192.168.0.66
Read from socket failed: Connection reset by peer
soultravel369@ANONYMOUS:~$ ssh -p 1369 soultravel369@127.0.0.1
Read from socket failed: Connection reset by peer
```Here is my port editing too... did I do something wrong?
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for, We liston to random port
Port 1369
```
My port is open too..
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:1369            0.0.0.0:*               LISTEN
```

---

### Post by lithopsian on 2011-03-17
Did you change the port on both machines?

You can also try setting the port back, just to double check that something else didn't get broken at roughly the same time.  It hurts so much when you hunt down a port problem for six hours and then find out you changed the key :)

Take a look in /var/log/auth.log for more details.

---

### Post by shane2peru on 2011-03-17
You only have to change the config on your box, not the box you are using to access that box.  However I think it would be best if you rebooted.  I think* but am not sure that just restarting sshd doesn't cut it.  Also you don't have any firewalls running do you?  They will block that port.  But you usually will get a different error.  Try a reboot on the box you are trying to get into.

Shane

---

### Post by SexySara on 2011-03-17
Thank you both very much!

Shane that was it... I had to reboot... who would of thought lol. Its the simple problems in life that are so hard and the hard ones are really the easy ones. Thank you!

---

### Post by shane2peru on 2011-03-17
Been there before.  There are other factors that play into that ssh stuff, and networking.  I don't remember what they all are, but glad it is working for you.

Shane

---

