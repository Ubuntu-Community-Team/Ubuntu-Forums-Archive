---
title: "Remote access of Linux server"
date: 2010-06-24
forum: General Help
---

### Post by satish_j on 2010-06-24
How can i access remote Linux server from an windows m/c and an Linux m/c??
All i have of server is its IP Address,username and password
I suppose the very 1st step here would be to establish the connection,which can be achieved thoufg ssh..

---

### Post by mike1821 on 2010-06-24
Through the Linux machine you can use ssh.

```
ssh user@ip
```

For the windows machine you can use PuTTy. It will also give you access into a remote console.

---

### Post by jbrown96 on 2010-06-24
you have to install an application on the server to allow you to connect to it... ssh, vnc, telnet, etc.

---

### Post by satish_j on 2010-06-24
> **jbrown96 said:**
> you have to install an application on the server to allow you to connect to it... ssh, vnc, telnet, etc.

Does it mean that the application installed at server will cause some service/daemon to be started that would listen for requests from client machines???
Also,you have specified some applications as examples...can PUTTY work for all these examples??

---

### Post by MedianMajik on 2010-06-24
You have the right idea.

example:  Running an SSH server on your home desktop allows you connect to it through an SSH Client on your portable laptop.  You use putty as a client, but I'm not sure it would work as a server.

---

### Post by satish_j on 2010-06-24
Iam sorry iam not good at networking,but how is it possible to connect 2 systems that are not in same domain and not connected(hard-wired)with each other??
If i install ssh server AND ASSIGN AN STATIC IP to my home PC,will i be able to access the same from office PC???
what all things will be needed??

---

### Post by jbrown96 on 2010-06-25
That depends on what type of static ip you have. If it's private (i.e. 192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12) [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network), then you will have to setup port forwarding on your router. That's for your server; the client doesn't matter.
If you have a public address, then you don't need to do any port forwarding. If you post the output of ```
ifconfig
``` we will be able to tell what type of ip you have.


After you figure out how to connect, then you need to decide what services you want. I don't know what you mean by "m/c". Ssh is pretty standard and you can install it with ```
sudo apt-get install openssh-server
``` Chkconfig is the best way to enable system services, so install it. Then automatically start ssh with ```
sudo service openssh-server start && sudo chkconfig openssh-server on
``` You might have to substitute sshd or ssh for openssh-server in the previous command. 

There's other services that you can run, depending on what you want to do. VNC can provide a remote desktop service, and there's lots of guides to help. FTP allows file access. Lots of others.

---

### Post by satish_j on 2010-06-25
No,iam not using static ip..iam planning to switch to it..And i suppose it is something that can be given by my ISP..
My final question is:
A working internet connection is required to connect to a remote server or not??
Iam not getting the flow of connection::I mean how does putty(or any other utility) connect to remote server??

---

### Post by jbrown96 on 2010-06-25
1) there needs to be a "route" between your client and server (i.e. an active internet connection). 

2) There has to be some type of server service (ssh, vnc, telnet, etc.) running on the server, so the client can connect to it.

---

