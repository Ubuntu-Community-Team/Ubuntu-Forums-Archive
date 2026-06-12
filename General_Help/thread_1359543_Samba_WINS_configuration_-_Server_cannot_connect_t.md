---
title: "Samba WINS configuration - Server cannot connect to clients"
date: 2009-12-19
forum: General Help
---

### Post by nicksvt on 2009-12-19
I posted this over on linuxquestions.org, but didn't get much help.

I am trying to configure my Samba server with WINS support.  I have gotten it working so that my Windows PCs can successfully register with the WINS database, and everything works from the windows clients' perspective.  I've verified that everything is as-expected in /var/log/samba/wins.dat.  

Unfortunately, I've been unable to get the server to be able to read from its own WINS tables.  Below is my smb.conf file, which is probably bloated as it is based off of the default configuration file.
```

[global]
    workgroup = MSHOME
    wins support = yes
    local master = yes
    domain master = yes
    preferred master = yes
    os level = 255
    dns proxy = no
    name resolve order = wins hosts lmhosts bcast

    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d

    security = user
    encrypt passwords = true
    obey pam restrictions = yes
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user

    usershare allow guests = yes

```My understanding is that to get NetBIOS host names to resolve, I need to have the name resolve order set above to include wins, as well as including "wins" in the /etc/nsswitch.conf file: 
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4
```In /var/lib/samba/wins.dat, there is an entry for the computer I am trying to ping:
```
"OFFICE#00" 1261254938 192.168.10.2 64R
"OFFICE#20" 1261254938 192.168.10.2 64R
```So when I type "ping office", nothing resolves.

I configured my Samba server to use a static IP so that clients could reach it.  This is my /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.10.3
        netmask 255.255.255.0
        network 192.168.10.1
        broadcast 192.168.10.255
        gateway 192.168.10.1

```My windows settings for the network connection are set to use a static ip address, with these settings:
        address 192.168.10.2
        netmask 255.255.255.0
        gateway 192.168.10.1

(not sure what the windows uses for network/broadcast, these aren't requested by the TCP/IP Properties menu under windows' network connections)

Any suggestions on other settings I may have to make or another place to look for help?  Let me know if more info is needed...

---

