---
title: "Setting a SSH socks proxy"
date: 2010-07-17
forum: General Help
---

### Post by tosszyx on 2010-07-17
A friend of mine is in a country with very restricted Internet access and ask me if I could help her to surf Internet freely. 

The easiest way to achieve this, is by setting up a simple SSH tunnel with SOCKS redirection and configure the programs in the client side to make use of it.

**CONFIGURATION**

The first thing to do is to install SSH:

```
sudo apt-get install ssh
```

Once installed, we should edit the **sshd_config** file, to secure our server and allow tunneling, sshd_config is the configuration file for the ssh server (as oppossed to *ssh_config*, that is in charge of the client).

First, we back up the original file:

```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bkp
```

With root power, we use a text editor (pico in this case) to modify the configuration file.

```
sudo pico /etc/ssh/sshd_config
```

It is widely recommended, to change some default options to disable root access, change the default port, enable the public key authentication and setup a list of the allowed user in our server, for more information about the options check the man page (**man sshd_config**, check notes below for some explanations).

```
PermitRootLogin no              #Disable direct login from root
AllowUsers user1 user2 user3    #*Only* allow this users to connect
AllowTcpForwarding yes          #Required to setup the tunnel
PasswordAuthentication no       #Disabled for better security
RSAAuthentication no            #Disabled to force DSA keys
PubkeyAuthentication yes        #Enables public key authentication
Port 8381                       #Listening port of the server
Protocol 2                      #Use only SSH protocol 2.
```

After saving the changes and closing the file, we should restart the ssh daemon to take on the new configuration:

```
user@server:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ]
```

Congrats! The SSH server is setup and ready to receive connection from the allowed users. We may have to forward the port configured for the server (in this case 8381) in our [wireless] router to our computer. 

**TEST SERVER**

To be able to test our new server, we have to first generate a DSA key pair to authenticate ourselves, we do this with the **ssh-keygen** command (*man ssh-keygen* for more information).

```
user@server:~$ ssh-keygen -t dsa
Generating public/private dsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_dsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/user/.ssh/id_dsa.
Your public key has been saved in /home/user/.ssh/id_dsa.pub.
The key fingerprint is:
bd:83:89:ba:6c:68:21:3e:78:55:9b:00:76:5e:75:c9 user@server
The key's randomart image is:
+--[ DSA 1024]----+
|       .....     |
|  o . .  .E      |
| . + .           |
|    o .  .       |
|     o oS .      |
|. . . o. o .     |
|o. +  . o o      |
|.o+...     .     |
| o..+.           |
+-----------------+
```

The passphrase chosen here is going to be needed to access the server, so we have to be careful and be able to remember it.

Now, in order for our server to know whom is allow to go in and whom not, we need to tell it the public keys of our accepted users, those, have to be listed in the file *~/.ssh/authorized_keys*, so we will append our newly generated key to it as follows (the key of every user that is granted access to server, has to be listed in this file):

```

user@server:~$ cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys
user@server:~$ cat ~/.ssh/authorized_keys 
ssh-dss AAAAB3NzaC1kc3MAAACBAPpJo2ZARwKDLasPy+9NDi87kVJDzn3O1sbWIoaxtD+mz9DRmp90Vcy0cIF0E/TIno8TXlOlCH1jqEAi8Kd3C+LfD3fdEvedsi+5a8GpsKpUsyS0nUtpCIJyXwwvrWfg5B5B2dNQMTnp+/sQaS1UCgfzxAvpItPRfYRRh+xGJrllAAAAFQC6wnp9PxBY7etnRUPvhgQWO6SAFQAAAIBDgbqBm/DpgKeecwKUyN6hIhM8aAWzFtOuCZtFpOaj0Kft7fqxRUIg/LYXp4O3iuvbHCMqNdr+tVoMrdM89Ki3jwe3cilylIbXbHPxqDRuT+RbrLVVgzrjJ9247LzPK5AYgMAScwhKGS+hCWrD+yHx9l0TMj2VKZSwYoSivExDGQAAAIEA8kerkz3TrwzovFT9hdK54MIHiuQh2j1f/5UA1d617DtaDBNhcr/tHm02WAs/xWve5h/YNowvk+fLUbsGln3iYWwZ1gnnmRQH+AvEPWOwYLtePe1cRp9s1nOlVpDyQOWRjAnE2W0aXttNDITmCDQlms2tMf+NMSmgamq3rnl0Rfw= user@server
```

To be able to test our configuration, we will use a service such as [http://whatismyipaddress.com/]("http://whatismyipaddress.com/") to find out our 'real Internet address' (as opposed to the LAN address) and try to connect to our server.

```

user@server:~$ ssh user@XX.XX.XX.XX -p 8381
Enter passphrase for key '/home/user/.ssh/id_dsa': 
Last login: Sat Jul 17 21:03:03 2010 from x.x.x.net
user@server:~$
```

It may not look very different to our normal prompt, but we are connected through SSH to our computer, to disconnect, we just have to type 'exit'.

```
user@server:~$ exit
logout
Connection to XX.XX.XX.XX closed.
```

**CLIENTS CONFIGURATION**

Now that our server is up and running and we test our ability to connect, we will setup our remote computer (friend's computer in unfriendly country ) to connect to Internet through our server.

We run the following command:

```
user@server:~$ ssh -D 7337 user@XX.XX.XX.XX -p 8381
Enter passphrase for key '/home/user/.ssh/id_dsa': 
Last login: Sat Jul 17 21:03:14 2010 from xx.xx.xx.net
user@server:~$
```

This command, create a tunnel in or local computer, listening in the port '7337' (or any other desired port), that will direct the traffic our server in the remote computer, located on XX.XX.XX.XX in the port 8381.

The -D option, specifies a local “dynamic” application-level port forwarding, so we don't have to setup tunnels for each application that we want to use. (more info in *man ssh*).

To setup Firefox to use this tunnel to navigate the internet, we go to Edit>Preferences>Advance in the Network tab, we click on the 'Settings...' button.

There we select "Manual Proxy Configuration" and leave everything blank, except for the field "SOCKS Host", where we write down the '127.0.0.1' and the port '7337', that is the configuration of our tunnel. We select the SOCKS5 option and save our configuration. 

As it stands, we now can use Firefox to navigate the web and our traffic will be forwarded through our tunnel, we can check that we are truly making use of our server, navigating a couple of pages and then kill our tunnel, not being able to navigate anymore.

With the current settings, even though our traffic is encrypted, our DNS request are still not being sent through our tunnel, to change this in firefox, we write in the address bar *about:config*, look for the key *network.proxy.socks_remote_dns* and change it to true.

Our SSH Tunnel, can be use with any program that can use a SOCKS proxy, such as Skype, messengers, etc. 

**NOTES**
1.- Why did we change the default port of our server? We change the default port of the SSH server, because there is a number of Bots/Scripts/'Hackers', testing the port 22 (default for SSH) with combinations of logins and passwords to try to gain access to our computer.
2.- Why did we disable root access to our server? See note 1
3.- Why did we disable RSA keys? See links below.
4.- Why did we enable just 'Protocol 2' ? See note 3.

**LINKS**
**To configure a windows client check**: [http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/]("http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/")
[http://www.devdaily.com/unix/edu/putty-ssh-tunnel-firefox-socks-proxy/index.shtml]("http://www.devdaily.com/unix/edu/putty-ssh-tunnel-firefox-socks-proxy/index.shtml")
**A tutorial to setup other kinds of tunnels as also SOCKS**: [http://www.verot.net/socks.htm]("http://www.verot.net/socks.htm")
[http://ubuntu-tutorials.com/2008/06/18/tunnel-web-and-dns-traffic-over-ssh/]("http://ubuntu-tutorials.com/2008/06/18/tunnel-web-and-dns-traffic-over-ssh/")
**How to create public keys in Putty (in case you use it) and why RSA keys are disable in this setup:** [http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html]("http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html")

---

### Post by b0n60 on 2010-08-14
Hi tosszyx, good work :)
But there's one thing I can't really understand:
> **tosszyx said:**
> 
**How to create public keys in Putty (in case you use it) and why RSA keys are disable in this setup:** [http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html]("http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html")
you disable the RSA Algorithm explicitly though the source you're refering to says this:
> **The PuTTY developers strongly recommend you use RSA**. **DSA has an intrinsic weakness** which makes it very easy to create a signature which contains enough information to give away the private key! This would allow an attacker to pretend to be you for any number of future sessions. PuTTY's implementation has taken very careful precautions to avoid this weakness, but we cannot be 100% certain we have managed it, and if you have the choice **we strongly recommend using RSA keys** instead.
so why do you want to force DSA keys???

---

### Post by randumnumber on 2010-11-20
This is a very useful tutorial, I am looking to do this exact thing. and i agree with the above. i will be using my RSA keys.

---

### Post by ibrahim.k on 2010-11-21
My ISP has blocked a lot of sites, how can I get connected to such server?

---

### Post by Brian96 on 2011-03-06
I am trying to set up an SSH SOCKS proxy like the one described here.  I used the instructions in this tutorial (although I used RSA and used the Ubuntu wiki on generating keys rather than the instructions here).  However, when I get to the "test server" step, the operation times out.

One catch is that I am testing this from my home LAN using the router's IP address (the router's firewall is configured to map the desired port to the desired port on the host machine).  In the test, I'm using the router's IP address (which is what I'll have to do when I'm using this connection while traveling). 

On the other hand, I can set up a connection just fine using the local LAN address for the host machine.

Any ideas of what might be wrong and/or how to test it?

Also, the desired port is listed as open using the port forwarding tester at yougetsignal.com

---

### Post by markeee on 2011-03-06
> **Brian96 said:**
> I am trying to set up an SSH SOCKS proxy like the one described here.  I used the instructions in this tutorial (although I used RSA and used the Ubuntu wiki on generating keys rather than the instructions here).  However, when I get to the "test server" step, the operation times out.

One catch is that I am testing this from my home LAN using the router's IP address (the router's firewall is configured to map the desired port to the desired port on the host machine).  In the test, I'm using the router's IP address (which is what I'll have to do when I'm using this connection while traveling). 

On the other hand, I can set up a connection just fine using the local LAN address for the host machine.

Any ideas of what might be wrong and/or how to test it?

Also, the desired port is listed as open using the port forwarding tester at yougetsignal.com
Not really , only thing I could suggest would be checking

hosts allow and deny

/etc/hosts.allow and /etc/hosts.deny

---

### Post by Brian96 on 2011-03-09
Not sure what my problem was, but it's working now.  The only difference I am sure of is that between my off-site tests, I changed from the default SSH firewall setting on my router to a custom one.  Don't know why that would matter, though.

---

