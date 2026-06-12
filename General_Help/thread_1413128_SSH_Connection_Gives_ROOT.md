---
title: "SSH Connection Gives ROOT"
date: 2010-02-22
forum: General Help
---

### Post by timecard on 2010-02-22
I recently installed OPENSSH server and client and so did my friend. We are using RSA and PUBKeyauth. When he logs into my SSH server he can use sudo without entering a password to modify any file on my computer. When i log onto his linux box i have to sudo and enter a password to modify any sort of file...
We are both logged into the user accounts that we are connecting to through ssh. Both my user password and root password are different.

Here is my sshd_config

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
PermitRootLogin no
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
PasswordAuthentication no

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

any sort of help or understanding of the problem would be nice.

---

### Post by Jackzor on 2010-02-22
> **timecard said:**
> I recently installed OPENSSH server and client and so did my friend. We are using RSA and PUBKeyauth. When he logs into my SSH server he can use sudo without entering a password to modify any file on my computer. When i log onto his linux box i have to sudo and enter a password to modify any sort of file...
We are both logged into the user accounts that we are connecting to through ssh. Both my user password and root password are different.

Here is my sshd_config

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
PermitRootLogin no
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
PasswordAuthentication no

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

any sort of help or understanding of the problem would be nice.

Sudo lasts for like 15 minutes. So. Try again after 15 or 20 minutes. Just don't use the computer till that time is up

---

### Post by gmargo on 2010-02-22
> **timecard said:**
> When he logs into my SSH server he can use sudo without entering a password to modify any file on my computer. When i log onto his linux box i have to sudo and enter a password to modify any sort of file.

You didn't say if **sudo** asks _you_ for a password on _your_ computer.  If it doesn't, then the behavior is consistent.

Probably his userid on your computer is a member of a group that is given permission by the **/etc/sudoers** file.  Check your's and his group memberships (use **id** command) against any authorized groups in **/etc/sudoers**.

---

### Post by timecard on 2010-02-22
ok ill try both these answers and get back to you thank you :)
You were right sudo was still giving access so i did sudo -k to kill my sudo after i needed to use it on my machine then my friend connected and he had to enter the password.

---

