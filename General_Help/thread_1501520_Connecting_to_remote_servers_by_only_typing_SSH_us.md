---
title: "Connecting to remote servers by only typing SSH user@ip"
date: 2010-06-04
forum: General Help
---

### Post by Isamtron on 2010-06-04
Hello,

I manage a few Linux servers and I need a fast way to connect to these servers instead of having to enter the root password every time.

Is there anyway to save the passwords/keys and connect to the servers by simply typing: SSH user@ip

Or even something easier without typing the server IP like I had Putty in Windows. I know I can still use Putty but I want to use a better SSH client, like GNOME Terminal.

Your help would be greatly appreciated.

---

### Post by ratcheer on 2010-06-04
The way I remember the command is: ssh -l username hostname

IP address may work in place of hostname.

Once the key has been stored, it should always remember it until something else changes.

Tim

---

### Post by Isamtron on 2010-06-04
Thanks but how and where can I store they keys?

---

### Post by Lucky. on 2010-06-04
[This link](http://linuxproblem.org/art_9.html) shows how to set up a passwordless SSH login by using public/private key pairs.  It worked pretty good for me!  However if you use this method, you won't be able to specify usernames when you log in.  Instead of "ssh user@ip", it's simply "ssh ip".

---

### Post by bodhi.zazen on 2010-06-04
1. Configure your ssh server to allow root logins without password

That is not what it appears :

[http://linux.die.net/man/5/sshd_config](http://linux.die.net/man/5/sshd_config)

> 
**PermitRootLogin**
Specifies whether root can log in using **[ssh]("http://linux.die.net/man/1/ssh")**(1). The argument must  be ''yes'', ''without-password'', ''forced-commands-only'' or ''no''.  The default is ''yes''.  


**If this option is set to ''without-password'' password  authentication is disabled for root.**


2. Make an ssh key for root and transfer it to the server.


3. When you log into the system, use ssh-add to add the key to ram.


4. You only enter your password once, when you first add the key. After that you simply


ssh server


and you will connect automagically.



This at least maintains some security.


I suggest you disable password logins and use iptables/denyhosts/fail2ban and/or tcp wrapper (deny.hosts) as well.

---

### Post by Isamtron on 2010-06-04
Thanks guys, it worked.

---

