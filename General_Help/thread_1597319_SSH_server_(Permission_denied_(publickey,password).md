---
title: "SSH server (Permission denied (publickey,password))"
date: 2010-10-15
forum: General Help
---

### Post by yankysunny on 2010-10-15
I am trying to install SSH server on my laptop. My laptop is connected to internet and it host a website.
I use noip to get my domain name working. Secondly, I dont want to use the authentication keys
So here is the problem,
When i installed ssh, it works with localhost, hostname(in a home network).
But it does not work with the domain
```
Permission denied (publickey,password)
```

Here is my sshd_config
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

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
#StrictModes yes

#RSAAuthentication yes
#PubkeyAuthentication no
#AuthorizedKeysFile    %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
#PermitEmptyPasswords yes

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
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM no
```

---

### Post by efflandt on 2010-10-15
Is your laptop directly on the internet with public IP on itself (not behind a router)?  If you are on a private IP behind a router, on the router you would need to forward port 22 to the LAN IP of your laptop.

And whether it is or not, are you trying to connect to the name that resolves to your public IP from the same computer.  Many routers (and Linux by default) do not do loopback (might not allow connection of LAN or other private IP on public interface, because that is a sign of IP spoofing).

So if you want to test public access to your server, do that from a computer on the internet, not the same computer or one on your LAN.  For example try to access it from a different dial up account, mobile data connection, or from a unix shell account on an internet computer.

PS: For sshd_config I NEVER allow root login, and use keys only.  If you want to leave your system open to password cracking, that is up to you.  But you might want to reconsider that once you get it working.  Note that your ~/.ssh should have 700 permission and any files in it should have 600 permission (ie, for you only).

---

### Post by yankysunny on 2010-10-16
Yes I am behind a router with private IP address.
and I did forward a port in my router but this password problems is still there.
Actually thanks very much for telling me for the risks involved for permisiions but I am just testing ssh to work. just an experiment and may be after that i will research on this more for permissions and keys.
One more question i wanna ask, As u told me that it may be a problem of port. so this permission denied is a error of port?is it?
secondly I will try from other computer if it works or not

---

### Post by yankysunny on 2010-10-19
Thanks very much..
I tried from another computer and it worked

---

