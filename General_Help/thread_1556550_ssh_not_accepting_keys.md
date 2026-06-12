---
title: "ssh not accepting keys"
date: 2010-08-19
forum: General Help
---

### Post by wannabegeek on 2010-08-19
hi all,
I posted this in Networks but have had little luck in that forum lately...

I haven't been able to connect via ssh to my media server at home. It's running Karmic (non-server version) and has sshd installed. I generated a rsa and dsa key pair and added them  to the server in   .ssh/authorized_keys and .ssh/authorized_keys2  by use of
cat  key >> .ssh/authorized_keys(2)

Changed sshd_config to only accept Keys and kept port 22, since I will port forward through router and make firewall exception down the line.

I made an account on the server with the same name as my laptop. Here's output from 
ssh -v daniel@10.0.0.10

[PHP]
daniel@Geek:~/.ssh$ ssh -v daniel@10.0.0.10
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.0.0.10 [10.0.0.10] port 22.
debug1: Connection established.
debug1: identity file /home/daniel/.ssh/identity type -1
debug1: identity file /home/daniel/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/daniel/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '10.0.0.10' is known and matches the RSA host key.
debug1: Found key in /home/daniel/.ssh/known_hosts:9
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/daniel/.ssh/id_dsa
debug1: Authentications that can continue: publickey
debug1: Offering public key: /home/daniel/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/daniel/.ssh/identity
debug1: No more authentication methods to try.
Permission denied (publickey).
[/PHP]
thanks you
wbg

---

### Post by Morrad on 2010-08-19
Hi there.

Would you be able to post your server's sshd_config file?

---

### Post by silbak04 on 2010-08-19
> **Morrad said:**
> Hi there.

Would you be able to post your server's sshd_config file?

Before you do what Morrad said, can you just run this in your terminal ```
sudo grep Port /etc/ssh/sshd_config
```and let me know what your output is

---

### Post by wannabegeek on 2010-08-19
thank you both for your interest

output of 
sudo grep Port /etc/ssh/sshd_config
[php]
ucky@lucky-desktop:~$ sudo grep Port /etc/ssh/sshd_config
[sudo] password for lucky: 
Port 22
lucky@lucky-desktop:~$ 
[/php]

which is what I hoped was set in sshd_config, which is below
[php]
lucky@lucky-desktop:~$ cat /etc/ssh/sshd_config 
# Package generated configuration file
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
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile   home/lucky/.ssh/authorized_keys

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
[/php]

---

### Post by Morrad on 2010-08-19
To me it looks like you're trying to log in as the user "daniel".

```
daniel@Geek:~/.ssh$ ssh -v daniel@10.0.0.10
```

The sshd_config code that you have attached, the ssh daemon is looking for the AuthorizedKeys file in

```
AuthorizedKeysFile   home/lucky/.ssh/authorized_keys
```

Unless you're specifically wanting only keys under the user "lucky" to be used, then you'll want to either comment out that line, or enter it as below (on my server, the following line is commented out).

```
AuthorizedKeysFile	%h/.ssh/authorized_keys
```

Give that a shot.

---

### Post by wannabegeek on 2010-08-19
thanks I will...I changed the name I was trying to login with...and I changed the directory that ssh looks for keys...but didn't square the two ... :)

gonna try now and post output....


yay !! it worked...that's a silly mistake, I tried a bunch of different stuff and didn't go back and cross check everything....
If I want to use a different account on the server, I suspect I'll have to copy the keys to that account's home.

Ultimately I am hoping to get access to this server from anywhere using DynDNS.com which I setup, but I think 
my router's firewall is preventing be from logging in. Do you mind trouble this issue as well ?

thanks to the forum once again,
wbg

UPDATE:
tried   $ssh -p XXXX [email]lucky@xxx.dyndns.com[/email]   and it worked!  but is this a good test since I am still at home behind router ? 
Does ssh to another computer at work, and then trying above connection make a better test ?

thx

---

### Post by Morrad on 2010-08-19
I'm glad you've solved the ssh issue.

I'd be willing to give a shot at helping with the DynDNS issue as well, but it might be a good idea to start a new thread for that others with more expertise on that topic will be able to more easily help you (the current title for *this* thread would make that difficult).

---

### Post by wannabegeek on 2010-08-19
ok...I'll start a new thread in general...thanks again

---

