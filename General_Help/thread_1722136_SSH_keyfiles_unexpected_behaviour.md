---
title: "SSH keyfiles unexpected behaviour"
date: 2011-04-05
forum: General Help
---

### Post by fast.fwd on 2011-04-05
Since this seems the right place to ask, I decided to register on this forum. I hope someone will be able to shed some light on my situation as I'm a bit in the dark about it.

I have a network with about half a dozen Ubuntu-machines and a similar number of Windows-clients. The Ubuntu machines are running either 10.04 or 10.10 in a mixture of 64- and 32-bit variants. I recently decided to build a new home-server and decided to go with 10.04 server 64-bit, since it'll be supported for awhile and i was pretty happy with my previous server that ran 10.04 32-bit, although it was a command-line install with a generic-kernel.

All my ubuntu-machines are accessible through SSH. Since I also run some rsync-scripts between them, I set up access through keyfiles, which are also used for the regular remote login. Password logins are completely disabled, so I specified *PasswordAuthentication no *and *UsePAM no *on all of them and it results in this behaviour:

```
user1@local:~$ ssh $IP
Permission denied (publickey).
```Which is what I would expect, and when I specify this:

```
user1@local:~$ ssh -i /path/to/keyfile $IP
```It logs me in without asking for anything, which is also as expected.

On my new server though, even though I set up /etc/ssh/sshd_config **exactly **the same as on all the other Ubuntu machines, I am not required to explicitly specify the location of the keyfile at all. I can simply do **ssh $IP **and it logs me in without asking for anything, no password, doesn't state I need a keyfile either.

It gives the Permission Denied message when I delete the ~/.ssh/authorized_keys file on the server, so there seems to be some kind of check going on, but on all other machines it doesn't work if I don't explicitly state the "-i /path/to/keyfile", so what is the difference here? 

Am I missing something? Is there an option that automatically searches  for a keyfile without specifying it explicitly that I don't know about,  or is this default behaviour for Ubuntu's server edition? And if so, how  do I change it? Because this doesn't exactly make me feel secure.

Contents of /etc/ssh/sshd_config (as it is on **all** Ubuntu-machines I have, including the server).

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

### Post by hawkmage on 2011-04-05
The configuration file of the ssh client is in /etc/ssh/ssh_config.  the /etc/ssh/sshd_config is the configuration for the SSH service/daemon.  

Also if the account has either ~/.ssh/id_rsa or ~/.ssh/id_dsa the ssh client will use this as the identity file without having to specify one.  If the public key of one of those ssh ID is in the ~/.ssh/authorized_keys for the account you are accessing you will be logged in as that user.

---

### Post by fast.fwd on 2011-04-06
> **hawkmage said:**
> The configuration file of the ssh client is in /etc/ssh/ssh_config.  the /etc/ssh/sshd_config is the configuration for the SSH service/daemon.  

Also if the account has either ~/.ssh/id_rsa or ~/.ssh/id_dsa the ssh client will use this as the identity file without having to specify one.  If the public key of one of those ssh ID is in the ~/.ssh/authorized_keys for the account you are accessing you will be logged in as that user.

Thanks for replying. I'm aware of what is what and what it does, the problem I'm having is that it logs me in without specifying a keyfile while connecting from the clients to the server, both ~/.ssh/id_rsa and ~/.ssh/id_dsa are not present on any of my systems.

Perhaps to clear things up a little, I'll provide a step by step sequence.

* On all my machines, I have a public key that is in ~/.ssh/authorized_keys.
* Also on all machines, logging in with passwords is disabled in /etc/ssh/sshd_config, making keyfiles the only option.
* To login from the client, I need to specify [COLOR=Blue]ssh -i /explicit/path/to/keyfile $IP-OF-HOST[COLOR=Black], where /explicit/path/to/keyfile equals the private key corresponding to the public one [/COLOR][/COLOR]in ~/.ssh/authorized_keys on the host.
* If, from the client, I specify the explicit -i option, it logs me in. If I do just [COLOR=Blue]ssh $IP-OF-HOST[COLOR=Black], it tells me [COLOR=Red]Permission denied (publickey)[COLOR=Black].

^^ That is the behaviour I have come to expect from the settings I use on all my machines for /etc/ssh/sshd_config, which I put in my starting post.

On my new machine though, even though those settings are exactly the same, on the client I can just specify [COLOR=Blue]ssh $IP-OF-HOST[COLOR=Black]. I did not specify any keyfile explicitly, but the connection is made regardless. It just logs me in without complaint, where I expected it would tell me permission was denied [/COLOR][/COLOR]unless I would explicitly state a private keyfile. It works that way on half a dozen machines I have running besides this.

The setup is exactly the same on all machines, from the options in both /etc/ssh/ssh_config and /etc/ssh/sshd_config, to the files in the ~/.ssh directories. So why is the behaviour of this new machine different and why does it accept a login **without** the -i option?
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by psusi on 2011-04-06
Why are you keeping the key outside of the normal location so you have to specify its path?  That is goofy.

Also the gnome keyring normally will cache the key and act as an ssh-agent, providing it to ssh automatically when it needs it.  You probably got it loaded into the gnome keyring.

---

