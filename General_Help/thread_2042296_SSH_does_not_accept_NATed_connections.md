---
title: "SSH does not accept NATed connections"
date: 2012-08-14
forum: General Help
---

### Post by natomb on 2012-08-14
Hello,

since update last weekend (did not do update for two weeks) I cannot connect via SSH from the Internet. I have setup port forwarding in my FritzBox and use a dyndns-address. Nothing was changed on FritzBox by me (i.e. no update, no configuration change). Furthermore, nothing was changed on the configuration of ssh server.

I am running a VM with Windows XP on the same machine, and I can connect via RDP to this virtual Windows XP instance. From there I can also connect via SSH. Thus, LAN connection to SSH is working. However, connection via SSH from the outside world is not working. There is also no connection attempt recorded in syslog.

Was there any new option introduced resulting in this behavior? Below, please find my sshd_config file:

Port 22
Port 64022
AddressFamily any
ClientAliveCountMax 10
ClientAliveInterval 30
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 2048
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
AllowGroups root adm nx
MaxAuthTries 2
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
RhostsRSAAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive no
MaxStartups 5:25:10
Banner /etc/ssh/welcome.message
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes

---

### Post by natomb on 2012-08-16
Hi,

I still could not resolve the problem. Meanwhile I changed LogLevel to DEBUG3 in the sshd_config file. The result is a lot of information written to /var/log/auth.log . However, when I attempt to ssh-connect from the Internet, there is not a single log entry. It appears that the connection request never reaches the SSH server.

To avoid any misconfiguration I also setup a new port forwarding at the FritzBox - kepping the old one unchanged. However, even with the new port forwarding entry things do not work. When changing from target port 22 (SSH) to target port 3389 (RDP) I can connect via RDP to the windows virtual machine.

Actually, I do not think that it is a problem of the server but rather the ISP I am using (1&1).

---

### Post by Zukaro on 2012-08-16
If port 22 doesn't work try changing the port SSH uses in your SSH configuration file to another port and then forward that port and try again.

---

### Post by Lars Noodén on 2012-08-16
Have you tried the obvious seeing if the ISP is allowing the connection through or blocking it?

[http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by rukiaEnix on 2012-08-16
LAN SSH connections work? And yes I think the first thing is what Lars says.

---

### Post by natomb on 2012-08-20
Hi,

indeed it was a problem with the ISP. Now, everything works just fine. Of course I tried to change ports. As not only me but also friends of mine could not connect, I am convinced that the ISP simply blocked any SSH-like traffic. Very strange what 1and1 wanted to do?

Regards
  Bjoern

---

