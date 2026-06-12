---
title: "FreeNX Authentication issues"
date: 2011-01-02
forum: General Help
---

### Post by MrDetermination on 2011-01-02
I have been through every how to and thread many times.  Current status:

SSHD config:
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
ServerKeyBits 4096

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
MaxAuthTries 5

RSAAuthentication no
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys
AuthorizedKeysFile	%h/.ssh/authorized_keys2
AuthorizedKeysFile2 /var/lib/nxserver/home/.ssh/authorized_keys2
AuthorizedKeysFile2 /var/lib/nxserver/home/.ssh/authorized_keys

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
#PasswordAuthentication no

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

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
IgnoreUserKnownHosts yes
PasswordAuthentication no
GatewayPorts no
AllowTcpForwarding yes
KeepAlive yes
ChallengeResponseAuthentication no
RhostsRSAAuthentication no
HostbasedAuthentication no
AllowUsers nx FRED

```

Result when connecting from NoMachine's windows client:
```
NX> 203 NXSSH running with pid: 3132
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.11 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: FRED
NX> 102 Password: 
NX> 103 Welcome to: blackbox user: FRED
NX> 105 listsession --user="FRED" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'FRED' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: FRED
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="pass" --type="unix-gnome" --geometry="1024x768" --client="winnt" --keyboard="pc105/en_US" --screeninfo="1024x768x32+render" 

Permission denied (publickey).
NX> 280 Exiting on signal: 15
```

In SSHD I can kill this line with no consequence:
AuthorizedKeysFile /var/lib/nxserver/home/.ssh/authorized_keys

If I comment this out:
AuthorizedKeysFile2 /var/lib/nxserver/home/.ssh/authorized_keys2

Then NoMachine gives me this error instead:
```
NX> 203 NXSSH running with pid: 3968
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.11 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

```

As root
client.id_dsa.key was moved to windows by:
cd /var/lib/nxserver/home/.ssh/
cp client.id_dsa.key /var/media/ (a SAMBA share)
and 
chmod 777 client.id_dsa.key
was needed to copy it out to windows
then that key was imported in to NM's client

client.id_dsa.key and the authorized_keys2 files were copied to /home/FRED/.ssh and no permissions were modified

SSH/Putty authentication works reliably with only this line in sshd:
AuthorizedKeysFile	%h/.ssh/authorized_keys

What am I missing?

This is 10.4, by the way.

---

### Post by MrDetermination on 2011-01-02
bump

---

### Post by MrDetermination on 2011-01-03
bump

---

### Post by MrDetermination on 2011-01-03
Solution found here:

[http://www.linuxquestions.org/questions/linux-networking-3/freenx-debug-help-with-authentication-791741/](http://www.linuxquestions.org/questions/linux-networking-3/freenx-debug-help-with-authentication-791741/)

"had to set authentication = SU in /etc/nxserver/node.conf. All other authentication methodes set to "0". Will hopefully get it on with custom keys now."

---

