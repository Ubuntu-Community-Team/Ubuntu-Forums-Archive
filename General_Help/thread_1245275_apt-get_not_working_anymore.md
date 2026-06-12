---
title: "apt-get not working anymore"
date: 2009-08-20
forum: General Help
---

### Post by alpharesearch on 2009-08-20
I need to use a proxy to get on the internet.

I use the proxy to send this message right now, looks like it works. However if I try sudo apt-get update I get this: 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  Cannot initiate the connection to 800:80 (0.0.3.32). - connect (22 Invalid argument)
(I get the same error on all lines)

Here is my proxy setting:
echo $http_proxy
140.200.11.94:800

This worked for years without problem... I did a reboot but no change... I guess the last update broke apt-get and also all other package managers like synaptic etc...

Please Help,
Markus

---

### Post by philinux on 2009-08-20
An old link. 

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

You might search the forums as this came up very recently.

Seen this as a solution too.
System > Preference > Network Proxy, set the proxy information there, told it to apply system wide and now it works!
[http://ubuntuforums.org/showthread.php?t=1007504](http://ubuntuforums.org/showthread.php?t=1007504) post #16

---

### Post by alpharesearch on 2009-08-20
Thanks... that fixed it. My new proxy export is now:
echo $http_proxy
[http://140.200.11.94:800/](http://140.200.11.94:800/)

I'm still not sure why it worked all this years without the [http:///](http:///) part???

Thanks,
Markus

---

