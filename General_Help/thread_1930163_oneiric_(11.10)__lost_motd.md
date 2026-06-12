---
title: "oneiric (11.10) : lost motd"
date: 2012-02-23
forum: General Help
---

### Post by magowiz82 on 2012-02-23
Hi,
since I was receiving continuously a warning in motd when I connect via ssh to an ubuntu machine that tells me that a certain partition will be checked on next reboot, I read in another post that the problem was with MOTD not being updated, and in that post it's suggested to delete /etc/motd , the problem is that now I don't get any motd but only something like :
```
No mail.
Last login: Tue Feb 21 18:19:38 2012 from *****
```

Is there a way to restore old motd ?

---

### Post by matt_symes on 2012-02-23
Hi

It sounds like pam is not genertaring your motd correctly for you when you log into your server and that maybe why you had the fsck message for so long (i assume it has ran fsck ?)

Please post the output of these commands from your server.

```
cat /etc/ssh/sshd_config
```

```
ls -l /etc/update-motd.d/
```

That is a small L after ls.

```
ls /var/run/motd
```

```
cat /var/run/motd
```

That will do for a start.

EDIT:

This is the contents of my servers /etc/motd file. As you can see, this is for 11.04 and not 11.10.

```

Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-13-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

Use "pastebinit" to copy a file, or output of a command to a webpage
allowing you to share it. e.g. 'pastebinit /proc/cpuinfo' or 'df -h |
pastebinit'
New release 'oneiric' available.
Run 'do-release-upgrade' to upgrade to it.


```

EDIT 2:

Ok. 

After a bit of digging on my server i can see that /etc/motd is a symbolic link to /var/run/motd

```

matthew@server1:~$ ls -l /etc/motd*
lrwxrwxrwx 1 root root 13 2002-01-01 05:48 /etc/motd -> /var/run/motd
matthew@server1:~$
```

/var/run/motd is generated my pam_motd everytime you log in so i would suggest it may either be pam_motd or the scripts in /etc/uodate-motd.d/ or the sym link.

That gives a starting point for debugging the problem.

Kind regards

---

### Post by magowiz82 on 2012-02-24
```
 cat /etc/ssh/sshd_config
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
PermitRootLogin no
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

``````
ls -l /etc/update-motd.d/
totale 32
-rwxr-xr-x 1 root root 1220 2011-07-15 00:13 00-header
-rwxr-xr-x 1 root root 1358 2011-07-15 00:13 10-help-text
-rwxr-xr-x 1 root root  159 2010-04-14 19:46 60-ubuntu-server-tip
-rwxr-xr-x 1 root root  149 2011-01-25 11:32 90-updates-available
-rwxr-xr-x 1 root root  129 2011-04-19 09:23 91-release-upgrade
-rwxr-xr-x 1 root root  142 2011-01-25 11:32 98-fsck-at-reboot
-rwxr-xr-x 1 root root  144 2011-01-25 11:32 98-reboot-required
-rwxr-xr-x 1 root root 1158 2010-10-21 15:04 99-footer

``````
ls /var/run/motd
/var/run/motd

``````
 cat /var/run/motd
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-16-generic i686)

 * Documentation:  https://help.ubuntu.com/

To deactivate a service at boot, for example, apache2: 'sudo update-rc.d -f
apache2 remove'. To activate it: 'sudo update-rc.d apache2 install
defaults'.


```


EDIT : sorry I read only after posting your edit, anyway I recreated /etc/motd as symbolic link to /var/run/motd , this solved the issue. Thank you! ;)

---

