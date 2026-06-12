---
title: "How to mount FTPS session (SSL) in Ubuntu 11.04?"
date: 2011-09-02
forum: General Help
---

### Post by jamesa00789 on 2011-09-02
Question says it all, I can't figure out how to do it. It must be something simple, but I can't find it.

I can't use Filezilla because I need SSL not TLS.

---

### Post by Lars Noodén on 2011-09-02
Are you in a position to work with SFTP instead? That would greatly expand the number of options available to you as well as simplify making the connection.

---

### Post by jamesa00789 on 2011-09-02
SFTP is not an option because as I understand it, it cannot be chroot'ed. Either way, there must be a simple way to do it since FTP is pretty much a standard way of transferring files?

---

### Post by Lars Noodén on 2011-09-02
[SFTP is easy to chroot](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads).  It requires only a single change in the configuration file for OpenSSH-server.

---

### Post by jamesa00789 on 2011-09-02
> **Lars Noodén said:**
> [SFTP is easy to chroot](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads).  It requires only a single change in the configuration file for OpenSSH-server.

I've tried that tutorial, however whenever I add the Match to the sshd config I get completely locked out from my server. I was lucky I had another way to change it back.

---

### Post by Lars Noodén on 2011-09-02
Your user has to be a member of the group that matches.  Then it will only be able to do SFTP not SSH.

---

### Post by jamesa00789 on 2011-09-02
Thank you lars for your help, but I'm giving up with this solution because I don't have the time to fix it.

Is there a simple way to mount FTPS? Everything works fine with windows since I can use WinSCP for FTPS, but for Ubuntu it doesn't seem to be so easy and I might just switch back to Windows which I really don't want to do!

---

### Post by jamesa00789 on 2011-09-06
So I have been browsing the internet and it seems there is no way to mount using FTP over an SSL connection?

If anything this is more of a security issue since FTP without SSL is very insecure so I hear.

---

### Post by Lars Noodén on 2011-09-06
I'd still recommend giving SFTP a try.  With it you can use SSHFS and mount the remote system as a folder on your local machine.

---

### Post by jamesa00789 on 2011-09-12
> **Lars Noodén said:**
> I'd still recommend giving SFTP a try.  With it you can use SSHFS and mount the remote system as a folder on your local machine.

Hi Lars,

I have tried this again but for some reason open ssh server locks me out completely and I cannot connect.

This is what I have done:

```
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp

Match User poker
    ChrootDirectory /home/poker
    ForceCommand internet-sftp

```

I have also tried the method of matching groups. It is a problem with the line Match.

I have updated my Ubuntu 10.04 server to the latest packages.

---

### Post by Lars Noodén on 2011-09-13
"internet-sftp" should read "internal-sftp"

When it works correctly, the user should be able to log in via SFTP but not regular SSH.

---

### Post by jamesa00789 on 2011-09-13
Thank you for your reply lars, much appreciated.

So I have tried this, and tried connecting through Filazilla using host: sftp://xxx.xxx.xxx.xxx with correct username, port and password with still no success. I'm going to post my entire sshd_config, see if you can spot anything.

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

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp

Match User poker
    ChrootDirectory /home/poker
    ForceCommand internal-sftp

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

#AllowUsers	james poker


```

---

