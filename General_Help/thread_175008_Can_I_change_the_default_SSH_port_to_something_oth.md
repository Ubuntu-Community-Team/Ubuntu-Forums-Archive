---
title: "Can I change the default SSH port to something other than port 22?"
date: 2006-05-12
forum: General Help
---

### Post by CzarAlex on 2006-05-12
Id like to use a different port than 22 for SSH`ing in to my box. How can I do that? :-k

---

### Post by jhorner on 2006-05-12
[QUOTE=CzarAlex]Id like to use a different port than 22 for SSH`ing in to my box. How can I do that? :-k[/QUOTE]

SSH default port is 22, change it through the above line, this will stop many automated attacks. Notice that when remotely connecting to the workstation, the new port number needs to be specified to the SSH client, for example:
$ ssh -p new port [email]username@host.doma[/email]in

found @ [http://aymanh.com/tips-to-secure-linux-workstation](http://aymanh.com/tips-to-secure-linux-workstation)

---

### Post by CzarAlex on 2006-05-12
Thanks! and thats just the reason why i want to change the port.

So I would do: ssh -p 1234 [email]username@host.doma[/email]in

or do I need to change [email]username@host.doma[/email]in to something?

---

### Post by jhorner on 2006-05-12
[QUOTE=CzarAlex]Thanks! and thats just the reason why i want to change the port.

So I would do: ssh -p 1234 [email]username@host.doma[/email]in

or do I need to change [email]username@host.doma[/email]in to something?[/QUOTE]

change the [email]username@host.doma[/email]in

to Username[whatever your username is]@host.domain [if your computer has a dns name then enter here; otherwise enter the IP addy.]  hope that helps.

---

### Post by DoktorSeven on 2006-05-12
To change the actual SSH daemon's listening port, edit **/etc/ssh/sshd_config** and change 

**Port 22**

to whatever port number you want, e.g.

**Port 1234**

Save and restart sshd:
**sudo /etc/init.d/ssh stop && /etc/init.d/ssh start**

Then use the -p option for the ssh client to connect to that port, substituting your computer's IP or name for **client**:

**ssh -p 1234 client**
(Or whatever port number you set above.)

---

### Post by CzarAlex on 2006-05-12
Perfect!! Thank you very much. Im up and running and more secure!

---

### Post by Slim Odds on 2006-05-13
[QUOTE=CzarAlex]Perfect!! Thank you very much. Im up and running and more secure![/QUOTE]

FYI, changing the port does **VERY LITTLE** to increase security. Automated scanners can easily find an ssh server on a different port.

The best way to increase security with SSH is to use a key-only access system. So that username/password guessing can't be used at all.

Read the docs.

---

