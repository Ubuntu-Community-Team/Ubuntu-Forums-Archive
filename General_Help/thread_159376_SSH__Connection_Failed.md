---
title: "SSH : Connection Failed"
date: 2006-04-12
forum: General Help
---

### Post by jhorner on 2006-04-12
First, I have searched many forums and google and have yet to find an answer to this problem.  I am wanting to use SSH on my ubuntu (home box) and connect using putty or ssh from a remote box (mainly XP).  I have installed the SSH and OpenSSH packages on my host box and enabled (started) the SSHD.  I have also opened the port 22 on my (harware, no software) firewall for both TCP and UDP access.  However, every time I try to connect to the host box, I receive a connection refused error.  

Host Box : Ubuntu 5.1
Remote Box : XP w/ SP2

Any Suggestions would be greatly appreciated.

---

### Post by sto6ma9ch on 2006-04-12
It sounds like you're either hitting your firewall and not getting through or you're not connecting to your firewall. 

Here is a list of things to check:

[LIST]
[*]Verify the external IP address of the firewall; this address is what you'll use to connect from your XP box
[*]Verify that your firewall is passing traffic from the firewall to the IP address of your Ubuntu box
[*]Verify on your Ubuntu box that SSH is listening on port 22 (should be by default)
[/LIST]
Let us know the outcome.

---

### Post by dave9191 on 2006-04-12
First of all make sure that ssh is working properly by conntecting from the ubuntu box to itself. 

From a command line:

ssh username@localhost


It will ask you for a password and then give you a typical prompt. If at this point it fails, then you haven't set up ssh properly or it's not running. If it is running properly then it's gotta be a firewall issue. 

--
Dave

---

### Post by jhorner on 2006-04-12
Verified the IP.  I even setup a dyndns account and that is how I also tried to access it.  
Firewall is passing all other traffic through.  
Verified that the SSH port is 22 (/etc/ssh/sshd_config).  
@dave9191, using localhost allows me to connect via ssh.  

thank you for the suggestions.

---

### Post by steve.horsley on 2006-04-13
Let's have s look at the ports the server is listening on. Can you do **netstat -plat**?

---

### Post by jhorner on 2006-04-13
I will give that a whirl when I get home tonite.  Thanks for the help.

---

### Post by jhorner on 2006-04-13
Here is what I got..

justin@etneral:~$ netstat -plat
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN     -
tcp        0      0 localhost.localdo:32771 *:*                     LISTEN     -
tcp        0      0 *:5900                  *:*                     LISTEN     7881/vino-server
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     -
tcp        0      0 192.168.2.2:47929       ohiggins.ubuntu.com:www TIME_WAIT  -
tcp        0      0 192.168.2.2:47928       ohiggins.ubuntu.com:www TIME_WAIT  -
tcp        0      0 192.168.2.2:47930       ohiggins.ubuntu.com:www TIME_WAIT  -
tcp        0      0 localhost.localdo:32770 localhost.localdo:55122 ESTABLISHED-
tcp        0      0 localhost.localdo:55122 localhost.localdo:32770 ESTABLISHED-
tcp        0      0 localhost.localdo:41459 localhost.localdoma:ipp ESTABLISHED7947/gnome-cups-ico
tcp        1      1 192.168.2.2:43768       rookery.ubuntu.com:www  LAST_ACK   -
tcp        0      0 localhost.localdoma:ipp localhost.localdo:41459 ESTABLISHED-
**tcp6       0      0 *:ssh                   *:*                     LISTEN     -**

Is that not the correct port??

---

### Post by jhorner on 2006-04-14
Just for anyone's information...

I went to the Apple Store today, and was able to connect via SSH from an iMac, but still unable to connect from the XP machine at work.  In someone else's opinion, would this be an issue with the guest machine / firewall???

Please advise, thank you.

---

### Post by dave9191 on 2006-04-14
Maybe the firewall at work is not allowing connections on port 22, I am assuming that the firewall you configured is at home and not at work. Or maybe this is just another example of MS software not working. 

--
Dave

---

