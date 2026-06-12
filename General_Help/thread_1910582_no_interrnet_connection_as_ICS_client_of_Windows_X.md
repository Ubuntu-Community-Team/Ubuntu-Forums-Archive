---
title: "no interrnet connection as ICS client of Windows XP"
date: 2012-01-17
forum: General Help
---

### Post by sbalfour on 2012-01-17
I've just done an upgrade to Kubuntu 10.10, over the internet as an ICS client of
Windows XP.  Then I also updated Windows.  Now I have no internet connection on
the client.  If I set up a ping to an outside IP address, the network monitors on
Windows and Kubuntu show lock-step incremental bytes sent/received on the
connected ethernet interfaces on the client and ICS machines.  So packets are
getting out, reaching the destination, and getting back to the client.  But the ping program
itself hangs, with 100% packet loss.  Likewise, Package manager times out
waiting for response and Icecat has no web access.  I can ping the subnet NIC on the
ICS machine from the client.  I also have ftp and rlogin connections operating between
them, so the network connections are robust.  ufw status is "inactive".    So where are
those packets getting lost? It appears that Kubuntu is somehow filtering packets not
originating on the subnet.

                                                      Stuart

---

### Post by jonobr on 2012-01-17
If you can ping the windows interface, then could you post the results of 
```
/etc/resolv.conf
```

also
can you ping 
74.125.224.80 
or put it in a browser and see what happens?
Lastly recommend you post ifconfig also for giggles

---

### Post by sbalfour on 2012-01-17
Pinging that IP address (as well as any other) results in ping program hanging 
waiting for response.  /etc/resolv.conf is empty.  It is not a DNS problem - neither
pinging nor browser access by numeric IP address results in anything but hang
waiting, or time out.  Packets are arriving on the Kubuntu machine's ethernet 
interface, but not getting back to the initiating program due to some kind of filtering.
But not all packets - I can ftp to the ICS server - just packets arriving from outside the
subnet.  Like a firewall, but there's no active firewall, and iptables have no such
filtering rules.  I'm a fairly experienced sysadmin - this isn't going to be something
ordinary. Something changed between Kubuntu 10.4 and 10.10 to do this.

                                                                    Stuart

---

### Post by jonobr on 2012-01-17
> I'm a fairly experienced sysadmin 

well then, good luck in your troubleshooting...

---

