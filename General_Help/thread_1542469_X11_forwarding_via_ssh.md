---
title: "X11 forwarding via ssh"
date: 2010-07-30
forum: General Help
---

### Post by sefa on 2010-07-30
Hi,

I am trying to run xeyes on a remote machine via ssh connection. Both my local and remote machines are Ubuntu 10.04. I connect to remote server via ssh -X and It does not forward to display to my local machine... 

```

root@goliath:/opt/install/bits# ssh -X -l root duke
root@duke's password: 
Linux duke 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Fri Jul 30 15:36:29 2010 from goliath.local
root@duke:~# env | grep DISPLAY
DISPLAY=:0.0
root@duke:~# xeyes &
[1] 3055
root@duke:~# ^C
root@duke:~# 

``` 



xauth is installed on the remote machine.

here is the /etc/ssh/ssh_config on the remote machine

```

root@duke:~# cat /etc/ssh/ssh_config

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
   ForwardX11 yes 
   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

Any ideas?

---

### Post by GlazedDonut on 2010-07-30
You should be editing /etc/ssh/sshd_config instead of /etc/ssh/ssh_config. Also restart sshd after saving changes to the sshd_config file.

---

### Post by sefa on 2010-07-30
Thanks for reply. Here is the /etc/ssh/sshd_config. I restarted the sshd,  still the same result...


See these two lines

X11Forwarding yes
X11DisplayOffset 10


is the offset supposed to be 10?



```

root@duke:/etc/ssh# cat sshd_config
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


```

---

### Post by GlazedDonut on 2010-07-30
Those lines are right. Depending on the network speed between the two machines, it mas take a while for graphical applications to load, especially if they are separated by the internet. Try waiting a few minutes after entering xeyes and see if anything pops up.

---

### Post by chopinhauer on 2010-07-30
> **sefa said:**
> 
```

root@duke:~# env | grep DISPLAY
DISPLAY=:0.0

```


It seems that something is messing with the DISPLAY variable on the remote machine. Have you checked if the shell initialisation files ~/.profile and ~/.bashrc (or less probably the system wide initialisation files /etc/bash.bashrc and /etc/profile) don't change the DISPLAY variable?

---

### Post by CharlesA on 2010-07-30
Hi there.

I tried your sshd_config file on a VM and ran ssh like this:

```
ssh -X ubuntu@192.168.1.30
```

It forwarded X over SSH fine. (it actually forwarded X11 from the VM to my server to my machine, but xeyes showed up on my end)

EDIT: Tried it from Ubuntu 10.04 x86 without any problems.

---

### Post by sefa on 2010-07-31
Hey chopinhauer, you were right there was a /root/.bashrc and had a export DISPLAY entry in it... I took the line out and everyting is working fine...

Thank you all for your help and responses

:popcorn:

---

