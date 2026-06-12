---
title: "Windows guy in need of a little help."
date: 2010-09-18
forum: General Help
---

### Post by Sunsoar on 2010-09-18
Hello all, ):P
I've been reading the forums as a guest to build myself my first ubuntu box (server).

Currently running : Ubuntu 10.04.1 LTS (virtual)
with : squid proxy with danguard.

Got it all work everything was sweet it had been working for a couple of weeks.
I've added some reporting and webmin in the last week but it was stable.
Anyway I  have clamav setup for content scanning, what seems to have occured is upon it's last update it has stopped dansguard from launching this was noticed overnight.

To fault find I've pointed my IE to squid proxy and port and it works.
If I point to Dansguard it doesn't
ps -A doesn't show dans working so I try and launch it and get the follwing error.
-----
 service dansguardian start
 * Starting DansGuardian dansguardian                                           Error daemonising
Exiting with error
                                                                         [fail]
------
So thinking about it I know I've setup claimav to do nightly updates and I know i've since patched the host that the virtual server is running on.

I migrated the host to my workstation and power it up reset the network interface settings and get the same error. Ok it's not the host. ( I iniatially built the virtual machine on my pc using vmware workstation, I now have it running on my windows home server with vmware player, so I know it did iniatially work on this pc.) 

So  backup my dans conf and edit away. I start by changing it's proxy port just in case something I've published is trying to use 8080 as well, no joy.

So I go and remark out clamav.
# contentscanner = '/etc/dansguardian/contentscanners/clamav.conf'
and presto the proxy is back and working.

-------
service dansguardian start
 * Starting DansGuardian dansguardian                                    [ OK ]

-----

How do I fault find this further which logs should I read to see why clamav is causing dans to now fail.
I'm happy to continue my reading just a generaly point in the right direction would be cool as google isn't helping me much with this.

Cheers

---

### Post by WorMzy on 2010-09-18
I'm not sure what dangaurd does, or how it works but shouldn't you put the path to the clamav executable after "contentscanner =", rather than the path to it's config file?

The executable should be either /usr/bin/clamdscan or /usr/bin/clamscan, depending on whether you want to use the daemon or not.

---

