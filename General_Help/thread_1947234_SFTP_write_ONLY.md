---
title: "SFTP write ONLY"
date: 2012-03-26
forum: General Help
---

### Post by Eiman on 2012-03-26
Hi all , we would like to create a "dropbox" user experiance using SFTP and Ubuntu, that user can upload files to a dir but not be able to read his own uploaded files (wirte-only), we did install ubuntu and SSHD, the SSHD_CONFIG looks like below ...
The user account44 is able to upload ( read, write ) files right now to the upload directory, but I want this user to only be able put files and not seeing them afterwards .
Can someone tell me how to achieve this for the user account44 ??
Thanks, 
 
 
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
# Logging
SyslogFacility AUTH
LogLevel INFO
# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile%h/.ssh/authorized_keys
# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes
# To enable empty passwords, change to yes (NOT RECOMMENDED)
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
Subsystem sftp internal-sftp
ChrootDirectory /sftp/%u
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp
 
#MaxStartups 10:30:60
#Banner /etc/issue.net
# Allow client to pass locale environment variables
AcceptEnv LANG LC_*
Subsystem sftp internal-sftp
ChrootDirectory /sftp/%u
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp
# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication. Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

---

### Post by gsgleason on 2012-03-26
remove read permission from the directory for that user.

---

### Post by CharlesA on 2012-03-26
> **gsgleason said:**
> remove read permission from the directory for that user.
That would do it. They would only need write and execute permission to browse that directory.

---

### Post by Eiman on 2012-03-27
Thanks for the message ...
How would I do that ? 
It should be only applicable for the user account44 .
Thanks, 
e

---

### Post by Eiman on 2012-04-10
[COLOR=black]What I ldid is logon with root account and then cd /sftp/account44/[/COLOR]
[COLOR=black]and then chmod -r upload [/COLOR]
[COLOR=black]Where upload is the directory which should have the dropbox effect , but when I ftp using account44 I cannot list the upload dir, which is good, but I cannot either write to it, getting [SIZE=1][SIZE=1]Directory /upload: permission denied ..[/SIZE][/SIZE][/COLOR]
[SIZE=1][SIZE=1][COLOR=black]What to do ?[/COLOR][/SIZE][/SIZE]
[SIZE=1][SIZE=1][COLOR=black]Thanks, [/COLOR][/SIZE][/SIZE]
[SIZE=1][COLOR=#ff0000][SIZE=1][COLOR=#ff0000][COLOR=black]e[/COLOR]
[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by CharlesA on 2012-04-10
Looks like you are trying to access /upload instead of /sftp/account44/upload

---

### Post by Eiman on 2012-04-11
How would i know that ? 
Thanks !

---

### Post by CharlesA on 2012-04-11
> **Eiman said:**
> How would i know that ? 
Thanks !
Says it in the error message:

```
Directory /upload: permission denied
```

Have you tested it with sftp?

---

### Post by Eiman on 2012-04-11
Dear Charles , 
Well I did use Filezilla using SFTP - SSH file transfer as protocol , the same error .
Still no joy ..

---

### Post by CharlesA on 2012-04-11
Try just using sftp itself from a terminal and see if it gives you any errors.

---

