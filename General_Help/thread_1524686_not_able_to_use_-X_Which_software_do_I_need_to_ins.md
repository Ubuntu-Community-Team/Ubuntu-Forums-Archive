---
title: "not able to use -X: Which software do I need to install?"
date: 2010-07-05
forum: General Help
---

### Post by shinokada on 2010-07-05
I can connect by using ssh with my server.

However I am not able to use the following. Which software do I need to install on the server?

ssh –X <username>@<IP address>
 

Thanks in advance.

---

### Post by bodhi.zazen on 2010-07-05
What problem are you having ? You should not need to install any additional software to forward X applications, although you may need to configure the ssh server to allow forwarding of X apps.

---

### Post by shinokada on 2010-07-05
> need to configure the ssh server to allow forwarding of X apps.     

Q1. Do I need to be the superadmin to use -X?

Q2. Where can I find the doc about changing config of ssh server?

Thanks in advance.

---

### Post by bodhi.zazen on 2010-07-05
> **shinokada said:**
> Q1. Do I need to be the superadmin to use -X?

No.

> Q2. Where can I find the doc about changing config of ssh server?

Thanks in advance.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by shinokada on 2010-07-05
1000 thanks.
:p

---

### Post by shinokada on 2010-07-05
I have the following config in sshd_config.

```
X11Forwarding yes
X11DisplayOffset 10
...

```

Do I need to change this??

++++++++++++++++++

Full code

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

---

### Post by bodhi.zazen on 2010-07-06
> **shinokada said:**
> I have the following config in sshd_config.

```
X11Forwarding yes
X11DisplayOffset 10
...

```Do I need to change this??

No.

---

