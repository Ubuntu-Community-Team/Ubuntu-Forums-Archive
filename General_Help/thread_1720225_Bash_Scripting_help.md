---
title: "Bash Scripting help?"
date: 2011-04-03
forum: General Help
---

### Post by conradin on 2011-04-03
HI all,
Im writing up a script to set up ufw with ssh on a user defined port.
I have 2 minor issues, 1, this script can only run once, from the defualt configuration files. if the config files are previously modified, this script will fail. So how can i fix it so that the line specifying port in the ssh_config file can be read and rewriten to numerous times. any ideas?

And 2, I have alot of echo type commands. how can I neaten that up?

```

#If these aren't installed, install them now with:
#sudo apt-get install openssh-server denyhosts ufw
#This script is to help you set up decent security
#on your Linux computers. Run this script as root. 
echo " select a port to forward ssh to Then hit ENTER"
read sshPort
ufw enable
sleep 4
 ufw default deny
sleep 4
 ufw allow $sshPort
sleep 4
 ufw logging on
sleep 4
clear
#echo "OK, Firewall is configured! Lets configure ssh!"
echo "Now we want to change how we respond to echo requests"
echo "Mom told me never to talk to strangers computers."
echo "I could write a function to search and replace but..."
echo "I'm going to be super lazy... instead."

sed -i 's/-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT/-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP/g' "/etc/ufw/before.rules"
sleep 3
sed -i 's/-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT/-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT/g' "/etc/ufw/before.rules"
sleep 3
sed -i 's/-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT/-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP/g' "/etc/ufw/before.rules"
sleep 3
sed -i 's/-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT/-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP/g' "/etc/ufw/before.rules"
sleep 3
sed -i 's/-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT/-A ufw-before-input -p icmp --icmp-type echo-request -j DROP/g' "/etc/ufw/before.rules"
sleep 3

echo "Ok Firewall Rules Set Goto www.grc.com -- shields up and test your firewall!"
echo "Now to set up the ssh Config file"
echo "First we will disable root Logins. "
echo " This is done because the most common attack on ssh"
echo "clients is for the root administration account."
echo "SSH Port is:" $sshPort
sed -i "s/22/$sshPort/g" "/etc/ssh/sshd_config"

sed -i 's/PermitRootLogin yes/PermitRootLogin no/g' "/etc/ssh/sshd_config"

echo ""
echo "When you want to log in to ssh use:"
echo "$ ssh -p " $sshPort " UserName@your-server-host"
echo ""
echo "I hope this script has made securing your open-ssh-server and firewall easier."
echo ""
echo "This script will now exit"
sleep 1
exit


```

---

### Post by andrewthomas on 2011-04-03
> **conradin said:**
>  if the config files are previously modified, this script will fail. So how can i fix it so that the line specifying port in the ssh_config file can be read and rewriten to numerous times. any ideas?
```

echo " select a port to forward ssh to Then hit ENTER"
read sshPort
echo "SSH Port is:" $sshPort
**sed -i "s/22/$sshPort/g" "/etc/ssh/sshd_config"**
sed -i 's/PermitRootLogin yes/PermitRootLogin no/g' "/etc/ssh/sshd_config"

```
The script will only replace the ssh port if it is currently set to 22.

Furthermore, what if the line is commented out?

I don't know about the version of sshd_config that Ubuntu ships, but the default values are usually stated and commented out, therefore changing the value without removing the # is pretty pointless.

```
#    $OpenBSD: sshd_config,v 1.82 2010/09/06 17:10:19 naddy Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.

#Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

# The default requires explicit activation of protocol 1
Protocol 2

# HostKey for protocol version 1
#HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 1024

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    .ssh/authorized_keys

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
ChallengeResponseAuthentication no
{cut rest of file ---}
```

---

### Post by conradin on 2011-04-03
Ubuntu doesn't ship with openssh-server, and yeah, I'm aware of the problem. What I would need is someway to find the line referring to port, and to re-write that line. Any ideas?

---

