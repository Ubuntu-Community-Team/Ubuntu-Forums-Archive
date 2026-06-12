---
title: "SSH requiring password, wasn't before"
date: 2010-10-25
forum: General Help
---

### Post by baddnady23 on 2010-10-25
I had SSH configured so that the keys were shared between my two machines and it didn't require a password to login and do maintenance.  Starting today, when I ssh into my file server, it is now asking me for the password.  This isn't good because it blocks my automated backup scripts from running...  Did something change with SSH recently or am I missing something?  I deleted the known_hosts and made a new one and it has not fixed anything.  Please help!   :confused:

---

### Post by spikoley on 2010-10-25
Maybe something happened to your /etc/ssh/sshd_config file.  Check it to see if the keys are enabled and disable the password if you want.

More on [sshd_config]("http://www.faqs.org/docs/securing/chap15sec122.html").

---

### Post by baddnady23 on 2010-10-25
thanks, i checked it on the server but that didn't seem to do it...

---

### Post by Serpher on 2010-10-25
Can you post the output of that file?

---

### Post by baddnady23 on 2010-10-26
> **Serpher said:**
> Can you post the output of that file?

```
 Package generated configuration file
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords yes

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
# PasswordAuthentication yes

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

---

### Post by baddnady23 on 2010-10-26
If it matters, the only thing that I have done with SSH in the past 5 days is log in remotely from a windows machine using putty and I had no problems doing it

---

### Post by spikoley on 2010-10-26
Try turning off PasswordAuthentication.

Change
```
# PasswordAuthentication yes
```
To
```
PasswordAuthentication no
```
Then run
```
sudo /etc/init.d/ssh restart
```

If that doesn't work then uncomment this line.
```
#AuthorizedKeysFile     %h/.ssh/authorized_keys
```
Then run
```
sudo /etc/init.d/ssh restart
```

---

### Post by cannywizard on 2010-10-26
Also, try enabling the debug output of the ssh command using
```

ssh -v myserver

```

---

### Post by baddnady23 on 2010-10-26
After making those changes to the sshd_conf, I get now get this:```
Permission denied (publickey).

```

Out put of ssh -v is:```
andrew@andrew-desktop:~$ ssh -v myserver
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /home/andrew/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
ssh: Could not resolve hostname myserver: Name or service not known
andrew@andrew-desktop:~$ ssh -v andrew-server 
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /home/andrew/.ssh/config
debug1: Applying options for andrew-server
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.70 [192.168.1.70] port 22.
debug1: Connection established.
debug1: identity file /home/andrew/.ssh/id_rsa type -1
debug1: identity file /home/andrew/.ssh/id_rsa-cert type -1
debug1: identity file /home/andrew/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /home/andrew/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.70' is known and matches the RSA host key.
debug1: Found key in /home/andrew/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/andrew/.ssh/id_dsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/andrew/.ssh/id_rsa
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by cannywizard on 2010-10-26
So, it just looks like the server isn't accepting your key.

In ~/.ssh/authorized_keys on the SERVER, there should be a list of the PUBLIC keys that are allowed to log in.

Your public key can (most likely) be found in /home/andrew/.ssh/id_dsa.pub on your LOCAL machine. 

It typically looks like 
```

ssh-(rsa, or dsa...), followed by a long list of characters.

```

There should be a matching line in the authorized_keys file on the server. If not, just copy and paste your public key into the sever file and try to log in again.

---

### Post by baddnady23 on 2010-10-26
> **cannywizard said:**
> So, it just looks like the server isn't accepting your key.

In ~/.ssh/authorized_keys on the SERVER, there should be a list of the PUBLIC keys that are allowed to log in.

Your public key can (most likely) be found in /home/andrew/.ssh/id_dsa.pub on your LOCAL machine. 

It typically looks like 
```

ssh-(rsa, or dsa...), followed by a long list of characters.

```

There should be a matching line in the authorized_keys file on the server. If not, just copy and paste your public key into the sever file and try to log in again.

They match :(  The only thing I did notice though is that at the beginning, it says ```
ssh-dss
```instead of either rsa or dsa.
Am I getting to the point where I should just remove SSH from the server and reinstall it?  I'm really confused how this happened seeing as I haven't changed anything on it in over a year.

---

### Post by baddnady23 on 2010-10-26
> **spikoley said:**
> Maybe something happened to your /etc/ssh/sshd_config file.  Check it to see if the keys are enabled and disable the password if you want.

More on [sshd_config]("http://www.faqs.org/docs/securing/chap15sec122.html").

Am I supposed to be editing this on the server or the client?

---

### Post by spikoley on 2010-10-26
> **baddnady23 said:**
> Am I supposed to be editing this on the server or the client?

The server.  Maybe this link will [help]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html").

---

### Post by baddnady23 on 2010-10-26
Well in sshd_config I changed```
StrictModes yes

``` to ```
StrictModes no

``` and it seems to be working now by not requiring the password.  Any other machine I log into with only the key has been working fine with the exception of this stubborn one.  Now the new problem is my rsync script is not working and that hasn't been changed at all, it was just fine before all this nonsense happened. :P

```
rsync -av --delete --exclude='/.gvfs/' --log-file=/home/andrew/Logs/rsync/2010/$(date +%Y%m%d)_rsync.log /home/andrew/ andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_desktop
notify-send "/home/andrew backup complete"
```

The output that I am getting in my log file is:```
2010/10/26 12:55:35 [8425] building file list
2010/10/26 12:55:35 [8425] rsync: opendir "/home/andrew/.Trash-0" failed: Permission denied (13)
2010/10/26 12:55:35 [8425] FATAL I/O ERROR: dying to avoid a --delete-during issue with a pre-3.0.7 receiver.
2010/10/26 12:55:35 [8425] rsync error: requested action not supported (code 4) at flist.c(1800) [sender=3.0.7]
```

---

### Post by spikoley on 2010-10-26
> **baddnady23 said:**
> Well in sshd_config I changed```
StrictModes yes

``` to ```
StrictModes no

``` and it seems to be working now by not requiring the password.  Any other machine I log into with only the key has been working fine with the exception of this stubborn one.  Now the new problem is my rsync script is not working and that hasn't been changed at all, it was just fine before all this nonsense happened. :P

```
rsync -av --delete --exclude='/.gvfs/' --log-file=/home/andrew/Logs/rsync/2010/$(date +%Y%m%d)_rsync.log /home/andrew/ andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_desktop
notify-send "/home/andrew backup complete"
```

The output that I am getting in my log file is:```
2010/10/26 12:55:35 [8425] building file list
2010/10/26 12:55:35 [8425] rsync: opendir "/home/andrew/.Trash-0" failed: Permission denied (13)
2010/10/26 12:55:35 [8425] FATAL I/O ERROR: dying to avoid a --delete-during issue with a pre-3.0.7 receiver.
2010/10/26 12:55:35 [8425] rsync error: requested action not supported (code 4) at flist.c(1800) [sender=3.0.7]
```

It sounds like the original issue is resolved.  You should start another thread for the new issue and mark this one Solved since it is a new issue.  You will end up getting more response that way.

---

