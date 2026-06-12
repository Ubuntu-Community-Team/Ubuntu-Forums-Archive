---
title: "Ports 111 and 738; ok to leave open?"
date: 2006-06-13
forum: General Help
---

### Post by MKR. on 2006-06-13
PORT    STATE SERVICE
111/tcp open  rpcbind
738/tcp open  unknown

I have a good idea of what RPC is for, but what is port 738?

I'm not too worried since I have a NAT router with no open ports incoming between me and anyone I would worry about, but I would like to know what they're for.

---

### Post by localzuk on 2006-06-13
Have you installed any software other than the basic set provided by Ubuntu? 

738 appears to be 'famd' which according to [http://www.linuxmanpages.com/man8/famd.8.php](http://www.linuxmanpages.com/man8/famd.8.php) is the File Alteration Monitor Daemon.

111 is rpcbind, which according to [http://www.scit.wlv.ac.uk/cgi-bin/mansec?1M+rpcbind](http://www.scit.wlv.ac.uk/cgi-bin/mansec?1M+rpcbind)  "is a server that converts  RPC program numbers  into universal addresses. It must be running on the host to be able to make  RPC calls on a server on that machine."

---

### Post by MKR. on 2006-06-13
[QUOTE=localzuk]Have you installed any software other than the basic set provided by Ubuntu? 

738 appears to be 'famd' which according to [http://www.linuxmanpages.com/man8/famd.8.php](http://www.linuxmanpages.com/man8/famd.8.php) is the File Alteration Monitor Daemon.[/QUOTE]

Looks like it was a false alarm; a scan from another computer revealed that both are part of nfs. I had enabled it for testing previously and forgot to undo the changes to my iptables policy.

Once I disalowed connections from the two hosts I allowed it from, the ports are no longer visible from outside. I'm double-checking with a more thourough scan, but it looks like the open ports were due to my own forgetfullness.

---

