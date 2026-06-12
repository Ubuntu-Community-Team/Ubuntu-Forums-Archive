---
title: "Using ssh instead of telnet"
date: 2012-03-04
forum: General Help
---

### Post by achuth on 2012-03-04
I have installed ubuntu 11.10.
We have a networked environment where there are 50 computers.
One of them is a server class machine.

For connecting to each of the 49 clients while sitting at the server, first I tried using **telnet**, but it disappointed me due to the fact that I have to install telnet servers in all the 49 clients before using telnet.

Now I am looking for **ssh.**

Do I need to perform some installation at the client side in order to make it **ssh** ready?

---

### Post by codemaniac on 2012-03-04
If you wish to access any server from any client system , Openssh server must be installed on the server and the ssh client needs to be installed on the client system from which you are going to access .

---

### Post by diesch on 2012-03-04
Even if you start the connection from your server this is technically the ssh client here and your client machines have to be ssh servers if you want them to accept ssh connections.

So you have to run a ssh server on any machine you want to connect to, just like with telnet or any other remote shell.

---

### Post by collisionystm on 2012-03-04
If your machines are windows you will need to use Putty or something similar.

---

### Post by codemaniac on 2012-03-04
> **collisionystm said:**
> If your machines are windows you will need to use Putty or something similar.
@collisionystm
Putty is merely an ssh client , installing putty wont let a system listen to incoming ssh connections .

---

### Post by llamabr on 2012-03-04
On the machine you want to login to:

```
sudo apt-get install openssh-server
```

---

### Post by Dave_L on 2012-03-04
Keep in mind that once you install openssh-server, you're vulnerable to attack via SSH, so make sure to configure sshd appropriately, and have other layers of protection such as a firewall.

---

### Post by collisionystm on 2012-03-04
> **codemaniac said:**
> @collisionystm
Putty is merely an ssh client , installing putty wont let a system listen to incoming ssh connections .




ahhh read it wrong. Thought the clients were trying to connect to the server.

---

### Post by collisionystm on 2012-03-04
You should 

A) Use Landscape and then you can sudo apt-get install ssh on all your boxes at once

B) Use Webmin cluster and do the same. 

Obviously you would have to install webmin and landscape on each machine individually the first time, however this will help you with future administration such as system updates and other programs. Landscape is the way to go....

---

