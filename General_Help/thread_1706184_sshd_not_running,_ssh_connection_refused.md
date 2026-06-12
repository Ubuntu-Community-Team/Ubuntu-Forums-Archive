---
title: "sshd not running, ssh connection refused"
date: 2011-03-13
forum: General Help
---

### Post by chrisandclem on 2011-03-13
Hi, I have been trying for weeks to solve this one and have researched everywhere I know to look.  Nothing has helped.  I am trying to ssh to my other machine (machine1=galla, machine2=cachin).  Both run Maverick Meerkat 10.10.  I get the following error when trying to ssh **to galla**:
ssh: connect to host galla port 22: Connection refused

uname -a outputs:
Linux galla 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

Also, sshd does not stay running.  I can start it, but a ps tells me it is never running.  I imagine herein lies the problem.  But why won't it stay running?

I am not running any firewall on galla (iptables -L told me that).

P.S. I ***can*** sucessfully ssh out of galla to cachin.  And, even if I just try to ssh localhost on galla, same thing happens.

Thanks in advance and I hope I posted this in the right place.

---

### Post by lithopsian on 2011-03-13
Examine /var/log/auth (on the remote machine) when you try to connect and see what it says.  Connections may be refused because of IP restriction, rejection of password authentication, wrong password, rejection of public or private key, or just ignored because of the wrong port.  All assuming the request is even reaching the remote machine.  Look in /etc/ssh/sshd_config to see what is allowed and what isn't.

I assume you have checked the sshd actually comes up and stays up?  Try restarting it manually before you test to make sure there are no funny messages.

---

### Post by llamabr on 2011-03-13
I assume you've already done:
```
sudo apt-get install openssh-server
```
?

---

### Post by chrisandclem on 2011-03-13
> **llamabr said:**
> I assume you've already done:
```
sudo apt-get install openssh-server
```
?
Yes, I even removed and reinstalled it once via synaptic.  And /usr/sbin/sshd is there....

---

### Post by gmargo on 2011-03-13
> **chrisandclem said:**
> 
Also, sshd does not stay running.  I can start it, but a ps tells me it is never running.  I imagine herein lies the problem.  But why won't it stay running?


Most likely a configuration error.  Check /var/log/syslog for errors.  

Have you modified the /etc/ssh/sshd_config file?  How does it compare to the machine that does work?

---

### Post by chrisandclem on 2011-03-13
Here's output from /var/log/auth file:

Mar 13 12:35:07 galla sshd[2204]: error: Bind to port 22 on 192.168.1.103 failed: Cannot assign requested address.
Mar 13 12:35:07 galla sshd[2204]: fatal: Cannot bind any address.
Mar 13 12:46:29 galla sshd[2222]: error: Bind to port 22 on 0.0.0.0 failed: Permission denied.
Mar 13 12:46:29 galla sshd[2222]: error: Bind to port 22 on :: failed: Permission denied.
Mar 13 12:46:29 galla sshd[2222]: fatal: Cannot bind any address.
Mar 13 12:46:43 galla sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/etc/init.d/ssh restart
Mar 13 12:46:43 galla sshd[2240]: Server listening on 0.0.0.0 port 22.
Mar 13 12:46:43 galla sshd[2240]: Server listening on :: port 22.

I made a change to the sshd_config file, commenting out this line:
#ListenAddress 192.168.1.103

That didn't help, but it did change the errors in the log file...

---

### Post by chrisandclem on 2011-03-13
I did see one error from rpc.imapd (not sure if it's related):

Mar 13 12:54:49 galla rpc.imapd[1057] nss_getpwname: name 'chris@downstay.com' does not map into domain localdomain

Incidentally, Both machine return "(none)" when I run domainname and downstay.com is not in my /etc/hosts file.

**Wooooooooo, I just got a new error:**

chris@cachin:~$ ssh galla
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
e8:38:b3:f1:7c:f2:d9:e3:f6:6d:cc:b0:18:9c:71:cd.
Please contact your system administrator.
Add correct host key in /home/chris/.ssh/known_hosts to get rid of this message.
Offending key in /home/chris/.ssh/known_hosts:1
RSA host key for galla has changed and you have requested strict checking.
Host key verification failed.

---

### Post by skada on 2011-03-13
could you provide /etc/ssh/sshd_config file ?

---

### Post by skada on 2011-03-13
Try changing stricthostkeychecking in ssh_config for the trial basis (its less secure)

---

### Post by gmargo on 2011-03-13
> **chrisandclem said:**
> 
Offending key in /home/chris/.ssh/known_hosts:1

You need to edit /home/chris/.ssh/known_hosts and delete line 1.

---

### Post by chrisandclem on 2011-03-13
> **lithopsian said:**
> Examine /var/log/auth (on the remote machine) when you try to connect and see what it says.  Connections may be refused because of IP restriction, rejection of password authentication, wrong password, rejection of public or private key, or just ignored because of the wrong port.  All assuming the request is even reaching the remote machine.  Look in /etc/ssh/sshd_config to see what is allowed and what isn't.

I assume you have checked the sshd actually comes up and stays up?  Try restarting it manually before you test to make sure there are no funny messages.

> **skada said:**
> could you provide /etc/ssh/sshd_config file ?

/etc/ssh/sshd_config:
chris@galla:/etc/ssh$ cat /etc/ssh/sshd_config
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 192.168.1.103
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
AuthorizedKeysFile	%h/.ssh/authorized_keys

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

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
UseLogin yes

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
UsePAM yes

AllowTcpForwarding no

---

### Post by chrisandclem on 2011-03-13
Slightly different error when I ssh to galla now:


chris@cachin:~$ ssh galla
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
e8:38:b3:f1:7c:f2:d9:e3:f6:6d:cc:b0:18:9c:71:cd.
Please contact your system administrator.
Add correct host key in /home/chris/.ssh/known_hosts to get rid of this message.
Offending key in /home/chris/.ssh/known_hosts:1
RSA host key for galla has changed and you have requested strict checking.
Host key verification failed.

---

### Post by chrisandclem on 2011-03-13
> **gmargo said:**
> You need to edit /home/chris/.ssh/known_hosts and delete line 1.

Did that, now the error is:
chris@cachin:~$ ssh galla
Warning: Permanently added 'galla' (RSA) to the list of known hosts.
Warning: the RSA host key for 'galla' differs from the key for the IP address '192.168.1.101'
Offending key for IP in /home/chris/.ssh/known_hosts:1
Ubuntu 10.10
Permission denied (publickey).

---

### Post by skada on 2011-03-13
backup .ssh/known_hosts to some other place and delete it.
Has server changed its RSA keys ?

---

### Post by chrisandclem on 2011-03-13
No, no change in the server's key.  I did get a new ~/.ssh/known_hosts file though on the client.

Incidentally, I am now getting a different error than when I started this thread.  And I get it whether I come in from another physical machine OR even if I ssh localhost:

Ubuntu 10.10
Permission denied (publickey).

---

### Post by lithopsian on 2011-03-13
Keys are messed up.  In your situation of limited connectivity, I'd wipe everything and start exchanging keys again.

---

### Post by chrisandclem on 2011-03-13
> **lithopsian said:**
> Keys are messed up.  In your situation of limited connectivity, I'd wipe everything and start exchanging keys again.

Thanks, could you give me a brief description of how exactly to do that (wipe everything and generate new keys)?

---

### Post by skada on 2011-03-13
odd is that keys of 'galla' differ from its ip address ! 
try this: delete the known_hosts file again and ssh using IP address rather than name.

---

### Post by chrisandclem on 2011-03-13
Got so frustrated (as I've made no sense of this for weeks) that I'm reinstalling Ubuntu!  Not so hard really since all my files were NFS'd from the other machine.  We'll see what ssh thinks about that!  I'll get back to you when I have up and running.  THanks!


***************************************************
Well, not an elegant solution, but re-installing Ubuntu fixed the problem.  Thanks everyone for your help!

---

