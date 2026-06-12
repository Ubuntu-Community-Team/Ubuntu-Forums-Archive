---
title: "Need to get a ufw file"
date: 2011-09-17
forum: General Help
---

### Post by jsvidyad on 2011-09-17
Hello,

  I use kubuntu 10.04 . I was editing the file /etc/ufw/before.rules and I made a mess of it. Unfortunately I didn't save a copy of the original unedited file. Is there some way I can get the original unedited file from the kubuntu 10.04 desktop installation CD? I put the CD in and searched for a file of that name in the CD without any success.

---

### Post by jsvidyad on 2011-09-17
Can someone please help me on this? If someone is running a kubuntu/ubuntu 10.04 system and has the unedited original file and can send that to me, that should be good enough too.

---

### Post by Dangertux on 2011-09-17
This what you're looking for?

```

#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -m state --state INVALID -j DROP

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

# allow MULTICAST, be sure the MULTICAST line above is uncommented
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```

---

### Post by jsvidyad on 2011-09-17
Yes, 

   Did you edit this file or is it the original unedited version?

Are you running (k)ubuntu 10.04??

---

### Post by Dangertux on 2011-09-17
This is unedited from 10.04 server.

---

### Post by jsvidyad on 2011-09-17
Thank You!!!

Hopefully it is the same for the desktop version too.

Can you do me a favor? Can you type the command
 dpkg -l | grep -i ufw

and give me the output of that? This is just so that I can make sure we are both using the same version of ufw.

---

### Post by Dangertux on 2011-09-17
Even if they aren't the same the default rules will be.

```

ufw                                 0.30pre1-0ubuntu2

```

---

### Post by jsvidyad on 2011-09-17
They are both the same version. Thank You for your help.

---

