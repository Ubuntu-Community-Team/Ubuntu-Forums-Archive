---
title: "Problem of node controller registration"
date: 2010-02-05
forum: General Help
---

### Post by Mehul on 2010-02-05
I have installed eucalyptus-cloud and eucalyptus-cc on one system and eucalyptus-nc on the other.

When i tried to connect nc with my cloud i was getting the following error.
The node is getting detected but it's not getting connected. Kindly reply as early as possible.

Also both CLC and CC are running on the server side and NC is also running on the client side. I checked that also.

>sudo euca_conf --no-rsync --discover-nodes

WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
Failed to resolve service 'smitha' of type '_eucalyptus._tcp' in domain 'local': Timeout reached
**New node found on 192.168.9.24; add it? [Yn] y**
--2010-02-05 23:30:02--  [http://127.0.0.1:8774/axis2/services/](http://127.0.0.1:8774/axis2/services/)
Connecting to 192.168.3.254:8080... connected.
Proxy request sent, awaiting response... 503 Service Unavailable
2010-02-05 23:30:02 ERROR 503: Service Unavailable.

ERROR: you need to be on the CC host and the CC needs to be running.

---

### Post by NehaM on 2010-02-11
I am having the same problem. 

**New node found on 192.168.192.81; add it? [Yn] y**
--2010-02-05 23:30:02--  [http://127.0.0.1:8774/axis2/services/](http://127.0.0.1:8774/axis2/services/)
Connecting to 172.20.0.99:8080... connected.
Proxy request sent, awaiting response... 503 Service Unavailable
2010-02-05 23:30:02 ERROR 503: Service Unavailable.

where 192.168.192.81 is the node cntroller and 172.20.0.99 is the proxy address.

Why is it trying to connect to the proxy? I am new to this. Kindly help.

---

