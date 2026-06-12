---
title: "Access files on home computer via SFTP"
date: 2011-06-01
forum: General Help
---

### Post by MagneticFlux on 2011-06-01
Hello,
I want to access my files on my home computer when I'm away (school, vacation etc). I set up a scheduled task to send to send me my external IP address by email because I have a dynamic IP and dont want a static url. (dyndns) I planned to use sftp for an encrypted connection, but I dont know where to start. How can I set up my computer to accept incoming requests, but without any security issues? Please include any router configuration needed.

Ubuntu 10.10 Desktop 32-bit
openssh-server installed

---

### Post by linuxinstalledfromhdd on 2011-06-01
Why don't you set up an SSH server instead? 

[http://cinderbox.net/2011/02/22/how-to-setup-ssh-on-ubuntu-10-10-maverick-meerkat-using-openssh-server/](http://cinderbox.net/2011/02/22/how-to-setup-ssh-on-ubuntu-10-10-maverick-meerkat-using-openssh-server/)

You are making it so much harder than this needs to be my friend. :)

---

### Post by MagneticFlux on 2011-06-01
That is probably what I want to do, but I dont want to just control the computer but to download files from it. Sorry if my previous post was a bit complicated.

---

### Post by doas777 on 2011-06-01
> **MagneticFlux said:**
> That is probably what I want to do, but I dont want to just control the computer but to download files from it. Sorry if my previous post was a bit complicated.
once you have ssh installed, you can just use winSCP on windows boxes to connect, or in gnome, open a window, hit Ctrl+ L to go into text mode, and issue a url like:
```
ssh://server/path/to/folder
```.

---

### Post by MagneticFlux on 2011-06-01
Do I need any router configurtion, eg port forwarding? And how can I change the defaulf port (22?) for extra security? How do I specify this new port from nautilus/winSCP? Is FileZilla an alternative to winSCP?
Thanks for the reply.

Edit: I learned that FileZilla *is* an alternative, more widely used I suppose.

---

### Post by linuxinstalledfromhdd on 2011-06-01
You can leave the computer on with Teamviewer 6 enabled and with your dynamic IP connection, and you can access the system from anywhere with Teamviewer 6. 

Check it my friend:

[http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/](http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/)

I use this all the time for exactly what you are doing the hard way.

---

### Post by MagneticFlux on 2011-06-01
> **linuxinstalledfromhdd said:**
> You can leave the computer on with Teamviewer 6 enabled and with your dynamic IP connection, and you can access the system from anywhere with Teamviewer 6. 

Check it my friend:

[http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/](http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/)

I use this all the time for exactly what you are doing the hard way.
Why does it need wine for? And which ports does it use?

---

### Post by linuxinstalledfromhdd on 2011-06-01
Because it works on other systems besides Linux natively. 

It has it's own wine cabs internally.  The PPA is just in case there are issues with some systems. 

Try it. See if you like it.  I'm not sure which ports. You would have to ask them.

---

### Post by doas777 on 2011-06-01
> **MagneticFlux said:**
> Do I need any router configurtion, eg port forwarding? And how can I change the defaulf port (22?) for extra security? How do I specify this new port from nautilus/winSCP? Is FileZilla an alternative to winSCP?
Thanks for the reply.

Edit: I learned that FileZilla *is* an alternative, more widely used I suppose.

for winscp, changing the port is easy (you'll see it when connecting), but with nautiuls you have to specify it after the server name in the url. 
```
ssh://test.example.com**:9999**/home/user1/Desktop/
```

FileZilla is indeed a tool you can use as an SFTP/SCP client. I haven't used it much, but my concern with it, is that first and formost it is an FTP client, and may not treat scp as well as it should. if it works well for you though...

also, if you ever want ssh based remote desktop functionality, look at FreeNX/NeatX. works great and is as secure as any remote access system. 

As for port fowarding, yes, you will need to forward incomming traffic for your ssh port in to your ssh server via nat/firewall rules.
this shoudl get you started:
[http://portforward.com/](http://portforward.com/)

---

### Post by MagneticFlux on 2011-06-02
I've set up port forwarding, but how can I try an ssh connection to my  machine from the same ip? How can I make the request come from outside?  Or should just entering my external ip work (did not)?

---

### Post by JCM_Pico on 2011-06-02
Configure DDNS in your router for that machine and create an account in [http://www.dyndns.com/](http://www.dyndns.com/)... and you will be able to access your pc anywhere

---

### Post by doas777 on 2011-06-02
if you wish to test your port forwarding configuration, try [http://canyouseeme.org/](http://canyouseeme.org/), and put in your port number. it will tell you if it appears open.

---

### Post by MagneticFlux on 2011-06-02
I do have a cron job that sends me my external ip every hour. I did not want to be bothered by a dyndns account, and I do not need a static url if I'm not going to share it (I suppose?). The command is:
```
curl icanhazip.com | mutt -s "MyIP" example@example.com
```and it works perfectly. (with some additional configuration for mutt and msmtp)

Now, my question is:
> **MagneticFlux said:**
> I've set up port forwarding, but how can I  try an ssh connection to my  machine from the same ip? How can I make  the request come from outside?  Or should just entering my external ip  work (did not)?

Edit:@#12, [http://canyouseeme.org/](http://canyouseeme.org/) can see me port 22.

---

### Post by doas777 on 2011-06-02
you should be able to connect to your Public IP at port 22. if (from an ubuntu machine) you enter in a terminal 
```
ssh <publicIP>
```
will it allow you to connect?
you may wish to try changing ports. my router denies inbound 22 to prevent wan side management. some comercial routers use firewall rules that are not always exposed to the user directly.

---

### Post by MagneticFlux on 2011-06-02
When I write only my ip, it prints my username and asks the password for it, but does not accept it.

---

### Post by doas777 on 2011-06-02
> **MagneticFlux said:**
> When I write only my ip, it prints my username and asks the password for it, but does not accept it.
ok. that means that ssh is up, and you can connect to it, but that it is denying your access.

can you post back:
```
sudo cat /etc/ssh/sshd_config
```

and you probably want to check your logs.

---

### Post by MagneticFlux on 2011-06-02
Sorry for the delay. Here is my /etc/ssh/sshd_config:
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
PermitRootLogin yes
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
Any ideas about where the problem could be?

Edit: How do I check my logs? If via Log File Viewer, which one?

---

### Post by MagneticFlux on 2011-06-02
bump

---

### Post by doas777 on 2011-06-02
in the log file viewer, check kern.log, syslog.log, and Messages.log. those should prolly do it.

ps: only bump if you've gone 24 hours without response.

---

### Post by MagneticFlux on 2011-06-02
What should I check for?

---

### Post by doas777 on 2011-06-02
> **MagneticFlux said:**
> What should I check for?
well,

I would look at the time, and make a login attempt. 
then hop to the server, and check all log entries since you made the login attempt. you're looking for any entry making reference to ssh, user login, or firewall logs.

---

### Post by MagneticFlux on 2011-06-02
How do I update the logs? And what do you mean by "hop to the server", I have only one machine if you missed it.

Edit: I think they are updated whenever something is written to them. There is nothing there about ssh, or at the time I tried to connect.

---

### Post by doas777 on 2011-06-02
ok.

any time you connect to somthing, you have a client and a server. they may be on the same box, or maybe not. either way, the messages you are looking for will be on the ssh server (if they in fact exist). if you are using the same box for client and server, then you are already there.

---

### Post by MagneticFlux on 2011-06-02
Fyi
> **magneticflux said:**
> 

edit: I think they are updated whenever something is written to them. There is nothing there about ssh, or at the time i tried to connect.

---

