---
title: "SSH Over internet"
date: 2011-04-30
forum: General Help
---

### Post by wane.dacha on 2011-04-30
A friend and I are running a server from his house.  We're trying to be able to run commands from it remotely (So I can run it when he's not available).  Ive got the IP address of his house, including the port forwarded to his computer. Also have the hostname and the login I want to use.  However, I can't get any commands to access.  Right now I'm using the format of ssh username@IP: port or ssh username@IP, but no go.  Any ideas?

---

### Post by epud on 2011-04-30
You might have already done this but:

make sure the port is forwarded to the computer you want to access. Most routers already have an ssh option you can associate with a computer.

On the computer you want to access you can try and ssh into the same computer. If that works there might be a problem with the connection.

make sure the username you use has an account on the PC.

---

### Post by epud on 2011-04-30
Oh I just remembered. If your friend does not have a static IP the IP address will keep changing all the time. An easy way to see what IP address your friend has, use his computer to visit: [http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by wane.dacha on 2011-04-30
I know the port is forwarded (though I'm not certain it is to his computer or just the server software)

I don't understand your second point...clarification?

Yes, I'm certain I have the user account name correctly.

Edit: Yes, Definetly sure about the IP.

---

### Post by epud on 2011-04-30
The global IP address of a computer usually changes on a regular basis as a security measure. A static IP address assures that the IP does not change with time. If you get your friend to give you his global ip and you try to ssh in straight away, you might have access and might be worth a try to see if the problem is that your friend has a dynamic IP and not a static one.

more info:
[http://www.wisegeek.com/what-is-a-static-ip-address.htm](http://www.wisegeek.com/what-is-a-static-ip-address.htm)

---

### Post by wane.dacha on 2011-04-30
Actually, just checked with my friend and he doesn't actually have the port forwarded--Just open.

Is there a way to bypass this?  Can I specify the target IP, target Port, target hostname and username?

---

### Post by epud on 2011-04-30
There is a way for bypassing not having a static IP. How it is done I am not sure. Think you will need a dynamic DNS. I use a static IP so it has not been a problem for me.

As far as I know he has to have the port forwarded to his machine for it to work, otherwise the router does not know which machine to forward the signal too. To forward the ssh port I choose "Assign a game or application to a local network device" on my router. Once that is done get your friend to quote you his IP and then give it a try.

If your friend is running ubuntu make sure your friend has the "secure shell client and server" package installed (you'll find it in the Ubuntu Software Center)

---

### Post by wane.dacha on 2011-04-30
Static IP isn't much of a problem, but thank you much for the port forwarding. And yes, I got the server package installed.

---

### Post by wlraider70 on 2011-05-02
Try running ssh in verbose mode

$ ssh -v username@ip

Also check out dyndns or something similar. It tracks you changing ip and continually updates it to a custom url so it would look like


$ ssh -v [email]username@alwaysuptodate.dyndns.org[/email]

---

### Post by rloc on 2011-06-27
Hi all, I have a similar question.

I have a Freebsd box and a Kubuntu box at home both on the same DSL router. The BSD box is running a mini website with Apache and I have FTP and SSH servers running and fully operational on this box as well. I now need to FTP and SSH the Kubuntu box via WWW but both the FTP and SSH clients link to the BSD box only. I am using Dyndns and have unique hostnames for each of the two servers. If I disable the FTP and SSH servers on the BSD box then I connect to the Kubuntu box so I know my config files are set up correctly.

What do I have to do to be able to access both boxes independently via WWW?

Any ideas would be much appreciated.

---

### Post by iclestu on 2011-06-27
> **rloc said:**
> Hi all, I have a similar question.

I have a Freebsd box and a Kubuntu box at home both on the same DSL router. The BSD box is running a mini website with Apache and I have FTP and SSH servers running and fully operational on this box as well. I now need to FTP and SSH the Kubuntu box via WWW but both the FTP and SSH clients link to the BSD box only. I am using Dyndns and have unique hostnames for each of the two servers. If I disable the FTP and SSH servers on the BSD box then I connect to the Kubuntu box so I know my config files are set up correctly.

What do I have to do to be able to access both boxes independently via WWW?

Any ideas would be much appreciated.

guessing you would need to use a different port for the new machine so ssh into one on port 22 and the other on port 220 or something? easy enough to ssh into a computer listening on a different port and you can set open ssh to listen on a different port by altering settings on /etc/*ssh*/sshd_config

---

### Post by Maheriano on 2011-06-27
The port needs to be forwarded. Nobody can help you until your friend forwards the correct port.

---

### Post by mixmaster on 2011-06-27
> **wane.dacha said:**
> A friend and I are running a server from his house.  We're trying to be able to run commands from it remotely (So I can run it when he's not available).  Ive got the IP address of his house, including the port forwarded to his computer. Also have the hostname and the login I want to use.  However, I can't get any commands to access.  Right now I'm using the format of ssh username@IP: port or ssh username@IP, but no go.  Any ideas?

err, isn't the ssh command:

ssh -p <portnum> user@ip

---

### Post by swmiller6 on 2011-07-01
I am having a similar problem. I can ssh into the server when on the local lan but I am unabe to connect remotely from work. 
I am not forwarding ports but I have the server setup in the DMZ aera of the router and I can connect to the server from a web interface via webmin, deluge web interface, and plex media servers web interface.

```
swmiller6@ubuntu:~$ ssh -v swmiller6@xx.xxx.xx.xx
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to xx.xxx.xx.xx [xx.xxx.xx.xx] port 22.
debug1: connect to address xx.xxx.xx.xx port 22: Connection timed out
ssh: connect to host xx.xxx.xx.xx port 22: Connection timed out

```

Copy of /etc/ssh/sshd
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 1,2
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
IgnoreUserKnownHosts yes

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
GatewayPorts no
AllowTcpForwarding yes
KeepAlive yes
Port 22

```

iptables
```
> lsmod | grep iptable
iptable_nat             3543  0 
nf_nat                 15560  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10346  3 iptable_nat,nf_nat
nf_conntrack           60943  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
iptable_filter          1369  1 
ip_tables               9899  2 iptable_nat,iptable_filter
x_tables               14175  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
```

---

### Post by arius13721 on 2011-07-01
You might want to find a service that performs port scans (I think I've seen one called GRC something or other) and scan the server with that to ensure that his ISP isn't blocking the port, or that yours isn't blocking it outbound, if you're sure the forwards are set up correctly.

/offtopic
> **epud said:**
> The global IP address of a computer usually changes on a regular basis as a security measure.

Sorry to get overly pedantic, but this is not correct. DHCP was created to automatically pass network configuration information to clients. 

And the reason or purpose of the changing IP address from the DHCP RFC: 

> Thus, dynamic allocation is particularly useful for assigning an address to a client that will be connected to the network only temporarily or for sharing a limited pool of IP addresses among a group of clients that do not need permanent IP addresses.

The only security inferred through an IP address change is security through obscurity.

---

### Post by swmiller6 on 2011-07-04
I figured this out..... Even though I had the server set in dmz zone of the linksys router I still needed to forward the proper ports for ssh to connect remotely. Adding it to the router configuration solved my problem.

---

