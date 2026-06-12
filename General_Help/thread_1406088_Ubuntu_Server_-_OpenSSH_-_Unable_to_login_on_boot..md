---
title: "Ubuntu Server - OpenSSH - Unable to login on boot."
date: 2010-02-13
forum: General Help
---

### Post by R3P1N5 on 2010-02-13
HP ProLiant DL380 G3 running Ubuntu Server 9.10 (karmic).

I am trying to initiate remote login via SSH using the latest PuTTY on my laptop (running Windows 7).

SSH has been configured to use DSA key authentication, and disallow password authentication.

When I attempt to do after the system boots, but before a user logs in, it returns the error "Server refused our key".

If I then log in on the server, and attempt to connect again on the client, it works! Even if that user then logs out on the server it still works.

How can I get OpenSSH to initiate properly on boot so that my remote login works without my user needing to have logged in.



Permissions on the .ssh files have been set as such:

```
drwx------ 2 usr usr 4096 2010-02-14 04:18 .
drwx------ 4 usr usr 4096 2010-02-14 04:28 ..
-rw------- 1 usr usr  602 2010-02-14 04:18 authorized_keys
-rw------- 1 usr usr  736 2010-02-14 02:28 id_dsa
```

My sshd_config file looks like this:

```
# What ports, IPs and protocols we listen for
Port 666
# Use these options to restrict which interface/protocols sshd will bind to
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts yes

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

```

Any help with this would be appreciated, I've been googling away trying to find a solution, but amongst the mess of 'how to set up ssh' tutorials... it can be tricky. It's probably something simple I overlooked, but for the life of me I can't spot it.

Thanks, let me know if you need any further information. I will check on this thread in a few hours time. I need some sleep :).

Having to log in before SSH works is the one thing stopping me from moving this machine to a remote, headless location.

---

### Post by zerosignal0 on 2010-02-14
So I havent been on the site in ages but I happened to be scrolling through and decided to make another account and lend some assistance.  Basically you are missing a couple of things in your config.  One of the majors is disabling "UsePAM".  This is a crucial step in getting your system to recognize that it is only to accept login credentials based upon your pub and priv keys.  Try making these 2 changes:

AllowRootLogin = No
PasswordAuthentication = No
UsePAM = No

As long as the public and private keys you have created are valid and are installed correctly on the server than you should have no problems.  Also you mentioned that you were connecting from a windows system so have you tried portaputty?  Its pretty cool to use with a windows client and can be used from any usb key, so mix that with truecrypt or any other descent hdd encryption software and your key will be safe wherever you go.

Also here is another link that does a good job going over the process start to finish in case my info doesnt fix things up for you.

[http://ubuntuforums.org/archive/index.php/t-30709.html](http://ubuntuforums.org/archive/index.php/t-30709.html)

Regards,
-Z

---

### Post by R3P1N5 on 2010-02-14
Thanks for the help, I'm out at the moment but I'll give it a shot when I get home.

---

### Post by R3P1N5 on 2010-02-14
Thanks for the help, found the problem after a lot more searching. Encryption was the issue. On install I selected that I wanted encryption on my $home directory, as such it was unreadable for ssh login until after a user had been logged in on the machine to decrypt the authentication files. Either moving the ssh authentication files or decrypting the $home directory would solve this issue.

See _[Can only connect to ubuntu server via SSH when logged in]("http://ubuntuforums.org/showthread.php?p=8323229")_ for further details on how to remove encryption.

-SOLVED!

---

### Post by samdavid on 2010-12-16
Hi , 

I have a DL580 G2 with ubuntu 10.10 installed . I am able to do remote iLO virtual power restart etc . But because I dont have advanced iLO i am not able to remote into the server . 

How did you setup ssh . So that you were able to remote ssh to the server from your laptop . 

Thanks
David

---

### Post by iqbalsajid on 2011-09-11
follow the link below to installation instructions for ssh on ubuntu 10.10

[http://cd-bills.blogspot.com/2011/09/how-to-install-ssh-server-in-ubuntu.html](http://cd-bills.blogspot.com/2011/09/how-to-install-ssh-server-in-ubuntu.html)

---

