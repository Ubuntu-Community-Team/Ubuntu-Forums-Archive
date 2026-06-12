---
title: "Use mdoem to dial in and ssh to another device"
date: 2012-06-05
forum: General Help
---

### Post by jay2068 on 2012-06-05
I have searched the internet and have yet to find anything on using a modem to dial into an ubutnu server then use ssh to another device. If anyone has any insight on what commands/software to use to do this please let me know. 
 
Thanks!

---

### Post by codemaniac on 2012-06-05
Have you configured your dial up modem in order to successfully connect to the internet ?
With an working internet connection and Openssh setup on the server , You can use the below commandline to establish ssh session to that server .
```
ssh *username@serverip*
```

Replace username and serverIP with yours .

---

### Post by jay2068 on 2012-06-11
I don't want the internet involved with this. :) 
 
I want my home computer (windows) to dial into a computer at work. Modem<->Modem connection. Then after the connection ssh into another device.
 
I know the ssh commands to connect to another device what I don't know is how to setup my Ubuntu Server to accept the inbound phone call/connection.

---

### Post by SleepWalkerX on 2012-06-11
Perhaps this is what you're looking for?

[http://ubuntuforums.org/showthread.php?t=150339](http://ubuntuforums.org/showthread.php?t=150339)

---

### Post by codemaniac on 2012-06-11
> **jay2068 said:**
> I don't want the internet involved with this. :) 
 
I want my home computer (windows) to dial into a computer at work. Modem<->Modem connection. Then after the connection ssh into another device.
 
I know the ssh commands to connect to another device what I don't know is how to setup my Ubuntu Server to accept the inbound phone call/connection.

To connect your home pc to your office network, you need the proper credentials from your network administrator to be able to log in through its VPN. However and internet connection is needed so that you can connect to the VPN .

---

