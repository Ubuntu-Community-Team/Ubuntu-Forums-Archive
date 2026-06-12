---
title: "nmap scan resulted in ftp, telnet, and http connection..."
date: 2010-08-08
forum: General Help
---

### Post by drink_stir on 2010-08-08
how do i block connections from a certian ip address?  i had a connection from an ip on port 10001 and i scanned it to see what it was and now theres all these connections from that ip. what should i do? i lock my firewall and it says the connections are still up...

---

### Post by gzarkadas on 2010-08-08
This will work regardless of the firewall you use, provided that you invoke the commands after the firewall start-up script finishes. It is great for manually adapting your firewall the moment you notice something; it requires though some work to incorporate it to your startup scripts (see below).

[U]Version 1: Just drop everything without logging:
[/U]```

sudo iptables -I INPUT -s [the-ip-address] -j DROP

```

[U]Version 2: Log before you drop setting limits to not fill your logs:
[/U]```

 sudo iptables -I INPUT -s [the-ip-address] -j DROP
 sudo iptables -I INPUT -s [the-ip-address] -m limit --limit 5/sec --limit-burst 8 -j LOG --log-prefix "known-bad-ip"

```

Replace the [the-ip-address] with the actual ip address you want to block.

If you have forwarding enabled in your machine (that is you use it as a  gateway to pass traffic to other computers) then you need to repeat one  more time the commands below replacing INPUT with FORWARD (for covering  the forwarding chain also).

Note (version 2) that because you are inserting rules in the top of your chain with those commands, sets of rules must be supplied in reverse order.

To incorporate the commands after the firewall start-up script finishes, you must first find where it is (different firewalls use different places, the most common being the /etc/rcS.d and /etc/init directories). Then either hack the script to append your commands or create your own to run *after* the stock script. You could also make a script in /etc/network/if-up.d. But it is usually easier to just add a command with your firewall UI; so if you need any help with this, please state the firewall that you use.

---

### Post by drink_stir on 2010-08-08
I use firestarter. and when i used sudo iptables -I INPUT -s [ip] -j DROP and in firestarter it still says there are active connections. do i need to edit the rules in firestarter?

---

### Post by gzarkadas on 2010-08-09
Insert the logging iptables command also and then check your logs to see if packets are dropped. You can also make a ```
sudo iptables --list-rules INPUT
``` and inspect the output to verify that indeed the blocking rule has been inserted. To see what are the connections use the following command ```
sudo netstat -tuapee
```; making your terminal window wide (132 chars) will help to review the output more easily.

It doesn't hurt to also put a rule in firestarter; after all you want your changes to become permanent.

---

### Post by drink_stir on 2010-08-09
it looks to be all clear. thanks. i put a rule in firestarter and checked with the --list-rules. notta sign...

---

