---
title: "SSH over internet not working"
date: 2009-12-31
forum: General Help
---

### Post by R3N3G4D3 on 2009-12-31
I just setup a media center PC for my parents using Xubuntu and installed SSH server on it (since they live in a different city, and I'll likely need to troubleshoot/update their PC occasionally).

The problem seems to be that I can ssh locally over the same LAN, but not when I use the external IP address. I already setup my NETGEAR router to forward port 22 to the media center PC, and checked online that my ISP isn't blocking port 22. When SSHing from local machine, I get into the media center PC just fine. When SSHing from local machine using external router's IP address I get "connection refused" message. My /etc/ssh/ssh_config has the following settings:
```

Host *
ForwardX11 yes
SendEnv LANG LC_*
HashKnownHosts yes
GSSAPIAuthentication yes
GSSAPIDelegateCredentials no

```

---

### Post by synapsys on 2009-12-31
Let's have a look at your etc/ssh/sshd_config

---

### Post by R3N3G4D3 on 2009-12-31
I didn't realize sshd_config was separate from ssh_config before. Here are the file contents (I don't notice anything that would block external connections here at first glance):
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
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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

### Post by R3N3G4D3 on 2010-01-01
Anyone? I also tried setting up vino and vnc4server, both work using local IP address but not using the internet address (forwarded ports 5900 and 5901 too).

---

### Post by t4thfavor on 2010-01-01
Try sshing from somewhere other than your network to your external IP. Most SOHO routers don't deal well with nat loopback.


As in, it will see the request as coming from your a private address to your public address, and block it.

Try from a friends house, and don't believe that your ISB is telling the trugh about what it's blocking and not blocking.

---

