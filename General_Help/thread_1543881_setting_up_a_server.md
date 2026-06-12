---
title: "setting up a server"
date: 2010-08-01
forum: General Help
---

### Post by philipballew on 2010-08-01
i am wanting to install ubunru server edition on an older sony vio desktop to use as a server i can access remotely. i will be needing to however access this server remotely from a college i attend throughout parts of the year. how exactly would i go about doing this?

---

### Post by CharlesA on 2010-08-01
SSH is always good, as long as it is secured properly.

Use a strong password and/or keys.

---

### Post by prodigy_ on 2010-08-01
+1 for SSH.

A good [place to start](https://help.ubuntu.com/community/SSH) with many useful links.

---

### Post by hakzsam on 2010-08-01
yes, reads this topic in order to install an openssh ssh server **[https://help.ubuntu.com/7.04/server/C/openssh-server.html](https://help.ubuntu.com/7.04/server/C/openssh-server.html)** :)

---

### Post by philipballew on 2010-08-01
whats the reason to do this instead of running say ubuntu server edtion of say a spare computer?

---

### Post by CharlesA on 2010-08-01
> **philipballew said:**
> whats the reason to do this instead of running say ubuntu server edtion of say a spare computer?

Huh? You use SSH to administer a server remotely.

---

### Post by NFblaze on 2010-08-01
I guess this all depends on what you are going to be doing remotely.

---

### Post by philipballew on 2010-08-01
sorry. so after i set up my ubuntu server edtion its best to then use ssh to accses the files and such?

---

### Post by CharlesA on 2010-08-01
If you need to access the files remotely, ssh can do that, since you can use sftp to transfer file to/from the server.

---

### Post by Joe of loath on 2010-08-01
For remote stuff I just use SSH. Almost everything can be done through it, so I don't see the point in screwing with my terrible router even more to get more services working.

---

### Post by philipballew on 2010-08-01
is there a guide that talks about how ti get ubuntu server edition set up in my house and how to run it and accsess it remotely?

---

### Post by CharlesA on 2010-08-01
> **philipballew said:**
> is there a guide that talks about how ti get ubuntu server edition set up in my house and how to run it and accsess it remotely?

There is a guide here: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

You would need to forward the port SSH uses on the router, so look at [www.portforward.com](www.portforward.com)

---

### Post by oldos2er on 2010-08-01
I'd probably start here: [http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

---

### Post by CharlesA on 2010-08-01
> **oldos2er said:**
> I'd probably start here: [http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

+1 to that as well.

---

### Post by philipballew on 2010-08-01
this looks quite complected to do from scratch, is it as complicated as it looks? about how long would this take?

---

### Post by CharlesA on 2010-08-01
> **philipballew said:**
> this looks quite complected to do from scratch, is it as complicated as it looks? about how long would this take?

It's not all that complicated, once it's installed you can connect by using the command with no further configuration needed.

If you count reading about ssh and understand what it is and what it does. It would probably take a day or so. If you just install it and read the pages linked, maybe a few hours to get it working.

```
ssh user@hostname
```

However, I really recommend setting a really strong password or using keys to prevent someone bruteforcing your password and compromising yer box.



To install openssh-server, run this in a terminal:

```
sudo apt-get install ssh
```

Then configure it by editing /etc/ssh/sshd_config (you can use whatever editor you want, I prefer vi, but nano, gedit, whatever works fine):

```
sudo nano /etc/ssh/sshd_config
```

Check out this for info on what each setting does:

```
man sshd_config
```

Here's what my sshd_config looks like:

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
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication no
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts no

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
**[COLOR="Red"]PasswordAuthentication no[/COLOR]**

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

# If specified, login is allowed only for user names that match one of
# the patterns.  Only user names are valid; a numerical user ID is
# not recognized.
**[COLOR="Red"]AllowUsers charles[/COLOR]**

# Specifies whether remote hosts are allowed to connect to ports
# forwarded for the client.
GatewayPorts no

# Specifies whether TCP forwarding is permitted.
AllowTcpForwarding yes
```

You can use it if you like, but be sure to change **"AllowUsers" to your username** and **"PasswordAuthentication" to yes**, if you want to use passwords.

I have mine set to "no" since I use keys instead of passwords, which is a bit more secure (no bruteforcing happens with keys). You can find out how to set them up [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

---

### Post by philipballew on 2010-08-02
ok. i have never done anything server related but what could it hurt

---

### Post by CharlesA on 2010-08-02
> **philipballew said:**
> ok. i have never done anything server related but what could it hurt

I would suggest installing Server in a VM and playing around with it before you install it on the physical machine. That way you will have a bit more experience with it.

I use [VirtualBox]("http://www.virtualbox.org/") for running stuff in VMs.

---

