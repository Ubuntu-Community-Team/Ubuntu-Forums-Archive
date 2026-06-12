---
title: "Can't open/parse the config file /etc/clamav/freshclam.conf"
date: 2010-03-11
forum: General Help
---

### Post by ardugh on 2010-03-11
Hi all,

I have installed ClamAV 0.95.3 into Ubuntu 9.10 (i386) fully patched
I am behind an authenticating proxy, so I've entered these details into freshclam.conf:
HTTPProxyServer myproxy.com
HTTPProxyPort 1234
HTTPProxyUsername myusername
HTTPProxyPassword mypass
- of course, I supplied the actual proxy details in the conf file.

When I run
$ sudo freshclam
I get :
WARNING: Insecure permissions (for HTTPProxyPassword): /etc/clamav/freshclam.conf must have no more than 0700 permissions.

So I changed the perms to 0700 (user is clamav).
Now I get:
$ sudo freshclam
ERROR: Can't open/parse the config file /etc/clamav/freshclam.conf


I checked DNS resolution with this (which I found in a thread somewhere):
# host database.clamav.net
database.clamav.net is an alias for db.local.clamav.net.
db.local.clamav.net is an alias for db.other.clamav.net.
db.other.clamav.net has address 193.1.193.64
db.other.clamav.net has address 130.59.10.36
- I presume the installation can find the update site?

What is wrong with my config, please?

Cheers,

---

### Post by dcstar on 2010-03-11
> **ardugh said:**
> Hi all,

I have installed ClamAV 0.95.3 into Ubuntu 9.10 (i386) fully patched
I am behind an authenticating proxy, so I've entered these details into freshclam.conf:
.........

Why?, your system has a Proxy setup section that applies to **all** applications.

---

### Post by ardugh on 2010-03-12
Thanks for your reply, dcstar.

I had enabled that proxy, but was still receiving errors from freshclam - can't remember the exact wording now. So I tried entering proxy details into freshclam.conf. Anyway, I removed them according to your reccomendation and changed the perms back so that freshclam.conf is parsed by clamav and ran:

# sudo freshclam
It's finding the network repository but failing to download:
<extract-1>
WARNING: getpatch: Can't download main-52.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download main.cvd
WARNING: getfile: Unknown response from remote server (IP: 130.59.10.36)
WARNING: Can't download main.cvd from db.local.clamav.net
</extract-1>

I'll keep trying

Cheers,

---

### Post by LtPitt on 2010-09-24
A

sudo dpkg-reconfigure clamav-freshclam 

made my day :)

---

### Post by somolinosfg on 2012-02-24
> **LtPitt said:**
> A

sudo dpkg-reconfigure clamav-freshclam 

made my day :)

Thanks a lot! It solved the issue for me too!

---

