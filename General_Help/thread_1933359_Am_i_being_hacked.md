---
title: "Am i being hacked"
date: 2012-02-29
forum: General Help
---

### Post by trillen on 2012-02-29
HI 
I am new to ubuntu and it looks like someone is trying to hack me can someone help please i would like to know how to stop this

thanks


copy from  Auth.log

```
ailed password for invalid user valerie from 58.27.225.206 port 44934 ssh2
Feb 27 20:41:51 bt sshd[6074]: Connection from 58.27.225.206 port 45274
Feb 27 20:41:52 bt sshd[6074]: Invalid user ric from 58.27.225.206
Feb 27 20:41:52 bt sshd[6074]: pam_unix(sshd:auth): check pass; user unknown
Feb 27 20:41:52 bt sshd[6074]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=58.27.225.206 
Feb 27 20:41:52 bt sshd[6074]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb 27 20:41:52 bt sshd[6074]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb 27 20:41:54 bt sshd[6074]: Failed password for invalid user ric from 58.27.225.206 port 45274 ssh2
Feb 27 20:41:55 bt sshd[6077]: Connection from 58.27.225.206 port 45610
Feb 27 20:41:57 bt sshd[6077]: Invalid user sgs from 58.27.225.206
Feb 27 20:41:57 bt sshd[6077]: pam_unix(sshd:auth): check pass; user unknown
Feb 27 20:41:57 bt sshd[6077]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=58.27.225.206 
Feb 27 20:41:57 bt sshd[6077]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb 27 20:41:57 bt sshd[6077]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb 27 20:41:58 bt sshd[6077]: Failed password for invalid user sgs from 58.27.225.206 port 45610 ssh2
Feb 27 20:41:59 bt sshd[6080]: Connection from 58.27.225.206 port 45900
Feb 27 20:42:00 bt sshd[6080]: Invalid user jessica from 58.27.225.206
Feb 27 20:42:00 bt sshd[6080]: pam_unix(sshd:auth): check pass; user unknown
Feb 27 20:42:00 bt sshd[6080]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=58.27.225.206 
Feb 27 20:42:00 bt sshd[6080]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb 27 20:42:00 bt sshd[6080]: pam_winbind(sshd:auth): pam_get_item returned a password

Feb 28 02:05:53 bt sshd[19994]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb 28 02:05:55 bt sshd[19994]: Failed password for invalid user dilbert from 58.27.225.206 port 63102 ssh2
Feb 28 02:05:55 bt sshd[19997]: Connection from 58.27.225.206 port 63465
Feb 28 02:05:57 bt sshd[19997]: Invalid user dollars from 58.27.225.206
Feb 28 02:05:57 bt sshd[19997]: pam_unix(sshd:auth): check pass; user unknown
Feb 28 02:05:57 bt sshd[19997]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=58.27.225.206 
Feb 28 02:05:57 bt sshd[19997]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb 28 02:05:57 bt sshd[19997]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb 28 02:05:58 bt sshd[19997]: Failed password for invalid user dollars from 58.27.225.206 port 63465 ssh2
Feb 28 02:05:59 bt sshd[20000]: Connection from 58.27.225.206 port 63799
Feb 28 02:06:00 bt sshd[20000]: Invalid user dookie from 58.27.225.206
Feb 28 02:06:00 bt sshd[20000]: pam_unix(sshd:auth): check pass; user unknown
Feb 28 02:06:00 bt sshd[20000]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=58.27.225.206 
Feb 28 02:06:00 bt sshd[20000]: pam_winbind(sshd:auth): getting password (0x00000388)
```

---

### Post by kousikmaiti on 2012-02-29
You can use firestarter.It is gui based firewall.

---

### Post by greenpeace on 2012-02-29
use keys to access your box over ssh and disable password-based logins.

There are a million tutorials around... this one seems to be fairly complete:
 
[http://www.g-loaded.eu/2005/11/10/ssh-with-keys/](http://www.g-loaded.eu/2005/11/10/ssh-with-keys/)

---

### Post by SlugSlug on 2012-02-29
install denyhosts

it blocks the IP address after about 5 failed login attempts

you could also shift ssh on to a different port to remove the majority of these attempts - but I find denyhosts enough :)

---

### Post by trillen on 2012-02-29
Thank you all for your reply's

---

### Post by winh8r on 2012-02-29
Rather than use firestarter which I believe is no longer maintained, you should install and configure GUFW which is an equally simple and effective firewall. It will allow you to set rules such as blocking repeated access attempts from a particular IP address.

have a look here:

[https://help.ubuntu.com/community/Gufw]("https://help.ubuntu.com/community/Gufw")

Hope this helps.

---

### Post by spynappels on 2012-02-29
+1 for denyhosts and using key based authentication rather than password authentication.

---

### Post by Gremlinzzz on 2012-02-29
sudo ufw enable
starts your fire wall
change old password
passwd in terminal

likely your neighbor using your WIFI connection,

---

### Post by Khayyam on 2012-02-29
> **Gremlinzzz said:**
> likely your neighbor using your WIFI connection,

Na, not unless the OP is in India (whois!) .. 

-1 for any solution not involving physical violence .. ummmm no ... +1 for blocking the offending (single) ip and then setting up key based logins.

I have the following script to deal with offenders like the above ..

```
#!/bin/bash

PATH=/sbin:$PATH; export PATH

# Usage: block-ip <address>[/mask]

IFACE="eth0"

# if the blocked file doesn't exist create it.
if [[ ! -f /etc/fw/blocked ]]; then
    touch /etc/fw/blocked
fi

# insert the rule at the head of the existing input chain 
iptables -I INPUT -i $IFACE -s $1 -m limit --limit 6/h --limit-burst 5 -j LOG --
log-prefix "IPTABLES BANNED: "

iptables -I INPUT -i $IFACE -s $1 -j DROP

# Append the new rule to the end of the blocked file
echo "iptables -A INPUT -i $IFACE -s $1 -m limit --limit 6/h --limit-burst 5 -j 
LOG --log-prefix 'IPTABLES BANNED: '" >> /etc/fw/blocked
```My iptables script then sources /etc/fw/blocked when called.

Your probably best to use a 'tool' for iptables (if your not familiar with) as suggested above.

HTH ... khay

---

### Post by trillen on 2012-03-03
> **Gremlinzzz said:**
> sudo ufw enable
starts your fire wall
change old password
passwd in terminal

likely your neighbor using your WIFI connection,

  Thank you all for your replyes  Its not the neighbor someone in England . My router only has password able to change cant change login is set to root "BUFFALO router"

---

### Post by matt_symes on 2012-03-03
Hi

> **trillen said:**
> Thank you all for your replyes  Its not the neighbor someone in England . My router only has password able to change cant change login is set to root "BUFFALO router"

Your trying to administer your router remotely ? If so then...

I flashed my router with dd-wrt so i could use keys on my router. I'm not suggesting you should flash your router as well as, if it goes wrong, you can brick your router.

I have bricked one router flashing with dd-wrt (power failure during transfer) and i lost the ability to even tftp a new flash image onto the router at router boot time. This make of router did not even have a jtag connector so the device was well and truly bricked.

That said, i am more than happy with my currently dd-wrt flashed router. 

I can use keys. Keys are much safer. I can ssh into it from anywhere and administer it with IP table rules and traffic control rules.

I am just relaying my experiences as opposed to offering any solutions above.

The only think i would suggest is use a very long and unpredictable password. Do not get stung by a dictionary attack. 

I would also change the default port number from 22 to something else. This will stop script kiddies and the number of ssh hits should fall.

Maybe you can also set up ip rules to drop ssh connection requests after a number of attempts in a period of time. This will depend on your router.

You can also set up rules to drop ssh attempts from blocks of ip addresses. If you live in Europe say, you can set up rules to block ssh connection attempts from outside Europe due to the way the IANA allocates ip addresses.

You never did specify your routers make and model.

Kind regards

---

