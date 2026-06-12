---
title: "Ubuntu server and security?"
date: 2006-05-15
forum: General Help
---

### Post by Jabran Asghar on 2006-05-15
Hello everyone,

I am setting up a Ubuntu Breezy 5.10 based server for following:
- DNS Server
- Email server
- Apache + Tomcat
- Samba (to manage some Ubuntu folder and files internal Windows network) 
- SSH (for remote logins from internal network)

Following is the network configuration:

(Pub-Net = public network, FW1 = Firewall1, Ubuntu = Ubuntu server, FW2 = Firewall2,  Loc-Net = Local network)

Pub-Net <----> FW1 <----> [Switch]

[From Switch]
|<----> Ubuntu 
|<----- FW2 <----> [Hub]
                                    
[From Hub]
|<----> Loc-Net

FW1 is configured to allow only following port forwarding to Ubuntu from public network
- SMTP (tcp port 25)
- POP (tcp port 110)
- Web server (tcp port 80)
- DNS (port 53)

FW2 blocks all connections from Ubuntu to local network.

SSH remote login is possible only from inside the local network as FW1 blocks external SSH remote connections.

Given the above scenario, could you please comment on:

- Do you see any security holes that above configuration may have? 
- What possibly can hack the above configuration to gain access to Ubuntu server, and even worst to - gain access to the local network?
- In all cases, what additional configuration/ideas could be to make the configuration more secure?
- How to do regular auditing of user logins and/or file accesses?

Thanks for any hints and suggestions.

Regards,
Jabran

---

### Post by glinsvad on 2006-05-15
All in all, security seems pretty tight regarding the public network...

- Do you see any security holes that above configuration may have? 
Well, I'm assuming that you have decent firewalls, but there is still the risk of intrusion "from within". I'm talkning viruses, trojans, poorly configured networking daemons and software susceptible to buffer-overflow-hacks, so limiting the administrative rights of user severely is a no-brainer (naturally, all binaries should be root-owned etc.). Also, install antivirus and system/network-monitoring on your server...

- What possibly can hack the above configuration to gain access to Ubuntu server, and even worst to - gain access to the local network?
Well, every open port is a potential gateway for a hacker. Most software have some vulnerabilities, usually related to memory-overflows, but they are hard for hackers to exploit without specific knowledge about the software/sourcecode. Once a hacker has gained access to the server, often they will introduce a worm or sniffer which sneaks past the firewall (FW2) in a call initiated from the local network. Not really sure how, but it is definitely do-able...

- In all cases, what additional configuration/ideas could be to make the configuration more secure?
I suggest limiting the ip-ranges thay may pass through FW1, if possible. Also, register MAC-addresses of all computers in the local network and disallow all other MAC-addresses to communicate with the Hub (or whatever).

Finally, make sure all passwords conform to a certain security standard (8+ in length, must include upper-, lowercase, numerical, space and special characters like _+-=,;.: etc.). This means root password cannot be "wizzard" :D

---

### Post by Jabran Asghar on 2006-05-16
Thanks for the reply :-)

[QUOTE=glinsvad]All in all, security seems pretty tight regarding the public network...

- Do you see any security holes that above configuration may have? 
Well, I'm assuming that you have decent firewalls, but there is still the risk of intrusion "from within". I'm talkning viruses, trojans, poorly configured networking daemons and software susceptible to buffer-overflow-hacks, so limiting the administrative rights of user severely is a no-brainer (naturally, all binaries should be root-owned etc.). Also, install antivirus and system/network-monitoring on your server...
[/QUOTE]

What are your suggestions for system-network monitoring? I am thinking of something that should do auditing of user logins, system reboots, and may be monitoring changes in certain system files? I know "last" command gives list of users who were logged into system in some past time but that limits to the log file size from which it gets that information. How can I increase the size of  the related log file so that it keeps information for user logins, lets say for last two weeks instead of only last one week?

Also I heard of Tripwire that does some kind for file auditing for changes, any suggestions regarding that?

[QUOTE=glinsvad]
- What possibly can hack the above configuration to gain access to Ubuntu server, and even worst to - gain access to the local network?
Well, every open port is a potential gateway for a hacker. Most software have some vulnerabilities, usually related to memory-overflows, but they are hard for hackers to exploit without specific knowledge about the software/sourcecode. Once a hacker has gained access to the server, often they will introduce a worm or sniffer which sneaks past the firewall (FW2) in a call initiated from the local network. Not really sure how, but it is definitely do-able...
[/QUOTE]

Can anyone can comment on this more please? 


[QUOTE=glinsvad]
- In all cases, what additional configuration/ideas could be to make the configuration more secure?
I suggest limiting the ip-ranges thay may pass through FW1, if possible. Also, register MAC-addresses of all computers in the local network and disallow all other MAC-addresses to communicate with the Hub (or whatever).

Finally, make sure all passwords conform to a certain security standard (8+ in length, must include upper-, lowercase, numerical, space and special characters like _+-=,;.: etc.). This means root password cannot be "wizzard" :D[/QUOTE]

I cannot limit IP addresses passing through FW1, as it will block recetption of emails and web server access from not-allowed IPs. But doing the same for internal logins to the server is already on my list.

Thanks for any further comments.

---

### Post by glinsvad on 2006-05-16
> What are your suggestions for system-network monitoring?

A place to start would be something like:
```

HISTFILE=~/.bash_history
HISTSIZE=10000
HISTFILESIZE=999999
# Don't let the users enter commands that are ignored in the history file
HISTIGNORE=""
HISTCONTROL=""
readonly HISTFILE
readonly HISTSIZE
readonly HISTFILESIZE
readonly HISTIGNORE
readonly HISTCONTROL
export HISTFILE HISTSIZE HISTFILESIZE HISTIGNORE HISTCONTROL

```
[http://linux.vlsm.org/share/Debian-Doc/manuals/securing-debian-howto/ch4.en.html]("http://linux.vlsm.org/share/Debian-Doc/manuals/securing-debian-howto/ch4.en.html")

Tripwire would work I guess, but I'm not sure which features a available in the open-source versions. I think the GPL alternative is something like acct.
```

sudo apt-get install acct

```

For some starting tips, check out:
[http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/firewalls.html#LOGGING]("http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/firewalls.html#LOGGING")
[http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/intrusion.html]("http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/intrusion.html")
[http://linux.vlsm.org/share/Debian-Doc/manuals/securing-debian-howto/index.en.html]("http://linux.vlsm.org/share/Debian-Doc/manuals/securing-debian-howto/index.en.html")

Also, I found this checklist helpfull:
[http://www.seifried.org/security/os/linux/20020324-securing-linux-step-by-step.html]("http://www.seifried.org/security/os/linux/20020324-securing-linux-step-by-step.html")

---

