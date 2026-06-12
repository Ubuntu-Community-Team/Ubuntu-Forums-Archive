---
title: "Few Questions on SSH keys"
date: 2011-07-17
forum: General Help
---

### Post by jaypadwick on 2011-07-17
Hello :)


I have setup working keys to my remove server but confused on one small detail.

When i ssh like this: ssh -i ~/.ssh/id-martin martin@server  - this works
When i ssh like this: ssh martin@server  - this does not work (access denied (public key))

I only ask because i have once before omitted the -i option and it worked fine.  Not sure what it depends on.


_Current setup below_

Remote server:

Hostname = server
Username = martin

added public key to: ~/.ssh/authorized_keys file
set permissions: chmod 700 ~/.ssh/authorized_keys

Contents of sshd_config

> # Package generated configuration file
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

UsePAM yesLocal machine:

Hostname = laptop1
Username = martin

added private key to: ~/.ssh/authorized_keys file
set permissions: chmod 700 ~/.ssh/authorized_keys




Any help of any kind is much appreciated :)

---

### Post by Lars Noodén on 2011-07-17
> **jaypadwick said:**
> ...I only ask because i have once before omitted the -i option and it worked fine.  Not sure what it depends on...


Maybe just that once you had loaded the key in to an agent using **ssh-add**?

---

### Post by jaypadwick on 2011-07-17
ah yes, i definitely used the agent before and not this time round.

hmm well ill google that,

cheers :)

(obviously would be cool if someone could point out how the agent does that)

---

### Post by Lars Noodén on 2011-07-17
Storing keys so you don't have to re-type the passphrase each time is what ssh-agent and ssh-add are for.

---

### Post by jaypadwick on 2011-07-17
yep just googled it, i remember now.

was years ago when i last did all this.

thanks for the tips :)

---

