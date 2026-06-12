---
title: "SSH logon delays"
date: 2011-08-23
forum: General Help
---

### Post by ofnuts on 2011-08-23
When I logon by SSH ("ssh me@somehost"), I experience an annoying delay (10-20s) before I'm asked for a password. For a while I considered it was a bad set up on the servers but I'm now interacting with a completely different set of servers and the problem remains.

The strange part is that I also use SFTP on the same servers (via KDE Dolphin) and I don't see this kind of connection delays using this method (whether I did a plain terminal connection before or not).

Are these delays expected/normal? If not what can I try to fix on my side?

---

### Post by ofnuts on 2011-08-29
bump...

---

### Post by Wim Sturkenboom on 2011-08-29
The ssh server is attempting to do a reverse lookup of the ip address that you connect from.

It might depend on your scenario but I had the problem when I configured a firewall; as a result, port 53 (if I recall correctly) was blocked.

You can also add an entry in the hosts file (if that suites your needs).

Reference
[http://www.linuxquestions.org/questions/slackware-14/iptables-slow-%5Bslackware-10-1%5D-452421/](http://www.linuxquestions.org/questions/slackware-14/iptables-slow-%5Bslackware-10-1%5D-452421/)

---

### Post by ofnuts on 2011-08-29
> **Wim Sturkenboom said:**
> The ssh server is attempting to do a reverse lookup of the ip address that you connect from.

It might depend on your scenario but I had the problem when I configured a firewall; as a result, port 53 (if I recall correctly) was blocked.

You can also add an entry in the hosts file (if that suites your needs).

Reference
[http://www.linuxquestions.org/questions/slackware-14/iptables-slow-%5Bslackware-10-1%5D-452421/](http://www.linuxquestions.org/questions/slackware-14/iptables-slow-%5Bslackware-10-1%5D-452421/)Hmmm. If the computer I connect to needs to do  a reverse lookup on my address, I don't see how opening ports on my system is going to help... I'm not running the name server. 

And, once logged in,  if I do a nslookup of my PC address, I get an answer (negative...) very fast, so I'd assume the SHH server isn't delayed by the reverse lookup? And why is it instantaneous in Dolphin?

---

### Post by seawolf167 on 2011-08-29
I've had problems due to DNS lookups.

edit the config file

```
gedit /etc/ssh/sshd_config
```

add this line at the bottom, save and exit

```
UseDNS no
```

restart the ssh service

```
sudo service ssh restart
```

try ssh'ing in now and see if you still have a delay

---

### Post by ofnuts on 2011-08-29
> **seawolf167 said:**
> I've had problems due to DNS lookups.

edit the config file

```
gedit /etc/ssh/sshd_config
```add this line at the bottom, save and exit

```
UseDNS no
```restart the ssh service

```
sudo service ssh restart
```try ssh'ing in now and see if you still have a delay
I'm connecting to a system for which I have no root privs... and the delays seem to be linked to using the ssh command on Linux. I have no such delays in the file manager, my Windows-based colleagues using PuTTY do no experince these delays either, I had the same delays with SSH working with a completely different set of machines (another project for another customer, with a different Linux on the target machines) so I have a hard time convincing myself that the problem isn't on my machine (or in SSH). In fact one of my colleagues did use Linux in the past and also remembers experiencing delays with SSH.

---

### Post by Wim Sturkenboom on 2011-08-29
> **ofnuts said:**
> Hmmm. If the computer I connect to needs to do  a reverse lookup on my address, I don't see how opening ports on my system is going to help... I'm not running the name server. 

And, once logged in,  if I do a nslookup of my PC address, I get an answer (negative...) very fast, so I'd assume the SHH server isn't delayed by the reverse lookup? And why is it instantaneous in Dolphin?

I shared my experience. I also posted a reference; read it (there is some debug info in there), apply it and see.

I'm not sure about sftp; it's a subsystem and might not do reverse lookup. Check the source code if you want to be sure :D

---

### Post by ofnuts on 2011-08-29
> **seawolf167 said:**
> I've had problems due to DNS lookups.

edit the config file

```
gedit /etc/ssh/sshd_config
```add this line at the bottom, save and exit

```
UseDNS no
```restart the ssh service

```
sudo service ssh restart
```try ssh'ing in now and see if you still have a delay

Actually you got me thinking. It's not the server that is trying to reverse-look me up, it my SSH trying to reverse-lookup the server. And I have a rather contrived DNS setup (two local and different names servers, plus one for a VPN that is often not there...). Adding  a few hosts in /hosts to avoid using the DNS does suppress the delay. 

Thanks for the heads up.

---

### Post by seawolf167 on 2011-08-29
Glad you got it working! :)

---

