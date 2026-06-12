---
title: "vpnc disconnects after about 8 hours"
date: 2011-02-13
forum: General Help
---

### Post by kb2001 on 2011-02-13
I've seen a problem staying connected to a Cisco VPN, this goes back a number of years

I was running 8.10 and it was fine.  After I moved to 9.10, the problem started happening.  My VPN connection to work would drop after 8 hours.  I looked around for a while and ended up compiling the cisco provided client which works fine (but is a pain).  I've been running 9.10 on my work laptop, and it experiences the same problem using vpnc, but I've been dealing with it because it's easier than using the Cisco client.  Recently, I installed 10.04 on my work desktop and the problem is still there.  This is extremely frustrating.

To check it, I installed 10.04 on my work desktop, my home desktop, and a personal laptop that was previously running 8.10, and all experience the same problem with vpnc.  I even go so far as to keep one terminal open with a constant ping all day and it still drops after about 8 hours.  A couple of others at work experience the same problem using vpnc.  This is not a problem using the Cisco provided client, or running it on windows or os/x

Has anybody else seen this, or have any ideas on what I can start looking for to get this addressed?  I'm at a loss on where to even start looking for what may be wrong.

---

### Post by kb2001 on 2011-02-20
Any ideas on what I can start doing to get more information about this problem?  I'm at a loss on even a starting point.  Any ideas would be much appreciated

---

### Post by nicksanders on 2012-05-11
[http://www.penlug.org/foswiki/bin/view/Main/CiscoVpn](http://www.penlug.org/foswiki/bin/view/Main/CiscoVpn)

Connection dropping after 8 hours

When using vpnc, the connection will always be dropped after it has been up for at most 8 hours, when rekeying occurs. This is because rekeying is not yet supported in vpnc, and Cisco's default rekey-intervall is 8 hours. Usually this is not too inconvenient, but you may want to consider using either GNU screen or TightVNC if you want to make sure you don't loose any state if you are disconnected unexpectedly. 

See also
[http://www.michali.org/general/70-fixing-vpnc-connection-drops](http://www.michali.org/general/70-fixing-vpnc-connection-drops)

---

