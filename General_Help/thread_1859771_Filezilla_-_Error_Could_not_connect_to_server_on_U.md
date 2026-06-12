---
title: "Filezilla - Error: Could not connect to server on Ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by beginer123 on 2011-10-14
I am a total beginner. I am working on a PC with installed Ubuntu 11.10 (upgrade 11.04)
 I want to install a phpBB3 forum on LAMP via FileZilla.
 I have a problem because Filezilla can not connect to the server.
 
This is a error from FileZilla
```
 Error: Could not connect to server 
``` I have installed LAMP. I can access the Apache2, MySQL and phpMyAdmin without any problems. I can access them.

 When I run the command
 ```
 sudo cat / etc / hosts 
``` I have the following situation
 ```

 beginer PCUbuntu1104 @: ~ $ sudo cat / etc / hosts
 [sudo] password for beginer:
 127.0.0.1 localhost
 127.0.1.1 beginer-name

 # The following lines are desirable for IPv6 capable hosts
 :: 1 IP6 IP6-localhost-loopback
 fe00:: 0 IP6-localnet
 ff00:: 0 IP6-mcastprefix
 ff02:: 1 IP6-allnodes
 ff02:: 2 IP6-allrouters
 beginer PCUbuntu1104 @: ~ $ 
``` My PC is static IP address 192.168.1.17 in LAN home network
 I tried to connect to localhost or Web server but without success.

 btw: I have been changed this line of code
 127.0.1.1 beginer-name

 What's the problem, can someone help

[edit]
I have correctly entered the username and password using this tutorial [http://www.youtube.com/watch?v=W9c8Q0VkW_Q](http://www.youtube.com/watch?v=W9c8Q0VkW_Q)

[edit2]
I also have this problem
 ```
 beginer PCUbuntu1104 @: ~ $ sudo-s
 **sudo: unable to resolve host PCUbuntu1104**
 [sudo] password for beginer:
 beginer @ PCUbuntu1104 :~$
```

---

### Post by beginer123 on 2011-10-14
> **beginer123 said:**
> 
[edit2]
I also have this problem
 ```
 beginer PCUbuntu1104 @: ~ $ sudo-s
 **sudo: unable to resolve host PCUbuntu1104**
 [sudo] password for beginer:
 beginer @ PCUbuntu1104 :~$
```I've just solved this problem so that I'm in '/etc/hosts' and '/etc/hostname' file put the same name (PCUbuntu1104).

Now it looks like this
I think that is OK :)
```
beginer@PCUbuntu1104:~$ sudo -s
[sudo] password for beginer: 
root@PCUbuntu1104:~# 

```Remains a problem connecting to the server via Filezilla ?

---

