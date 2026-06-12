---
title: "Cloud Eucalyptus Node Not Recognized"
date: 2009-12-22
forum: General Help
---

### Post by brookstevens on 2009-12-22
Hi,
I am new to ubuntu enterprise cloud and Eucalyptus and trying to get a simple test environment up.  I got everything installed, but the Node is not recognized.  I don't get any error message but it is not showing in the euca-describe-availability-zones  verbose command...perhaps I just don't understand what I am looking at though.
Here is the output of the discover nodes command:

sudo euca_conf --no-rsync --discover-nodes
New node found on 192.168.30.110; add it? [Yn] Y
--2009-12-22 12:12:10--  [http://127.0.0.1:8774/axis2/services/](http://127.0.0.1:8774/axis2/services/)
Connecting to 127.0.0.1:8774... connected.
HTTP request sent, awaiting response... 200 OK
Length: 730 [text/html]
Saving to: `STDOUT'

100%[========================================================================================================================>] 730         --.-K/s   in 0s      

2009-12-22 12:12:10 (22.4 MB/s) - `-' saved [730/730]


INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.
warning: //var/lib/eucalyptus/keys//node-cert.pem doesn't exists!
warning: //var/lib/eucalyptus/keys//node-pk.pem doesn't exists!


Trying scp to sync keys to: eucalyptus@192.168.30.110://var/lib/eucalyptus/keys/...
Warning: Permanently added '192.168.30.110' (RSA) to the list of known hosts.
done.
--------------------------------------



And here is the output of the output of the euca-describe-availability-zones  verbose command after the above was executed:

--------------------------------------
euca-describe-availability-zones  verbose
AVAILABILITYZONE	Testbed02	192.168.30.100
AVAILABILITYZONE	|- vm types	free / max   cpu   ram  disk
AVAILABILITYZONE	|- m1.small	0000 / 0000   1    128     2
AVAILABILITYZONE	|- c1.medium	0000 / 0000   1    256     5
AVAILABILITYZONE	|- m1.large	0000 / 0000   2    512    10
AVAILABILITYZONE	|- m1.xlarge	0000 / 0000   2   1024    20
AVAILABILITYZONE	|- c1.xlarge	0000 / 0000   4   2048    20

--------------------------------------
I have nothing in the error log and I don't see anything obvious in any of the other logs.  Thanks for any help.

---

