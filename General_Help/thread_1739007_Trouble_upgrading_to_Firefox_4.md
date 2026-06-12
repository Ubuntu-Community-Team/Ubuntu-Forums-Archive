---
title: "Trouble upgrading to Firefox 4"
date: 2011-04-25
forum: General Help
---

### Post by laredotornado on 2011-04-25
Hi,

Here's my version ...

uname -a
Linux administrator-OptiPlex-745 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

Per another thread on the forum, I tried upgrading to firefox 4 and am getting this error

selenium@administrator-OptiPlex-745:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Any ideas or alternatives for upgrading to Firefox 4? - Dave

---

### Post by lithopsian on 2011-04-25
A temporary problem with the keyserver?  You can download Firefox 4 directly from mozilla.org but then you won't be able to maintain it through the package manager.

---

### Post by lovinglinux on 2011-04-25
See [Firefox 4 Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247"). There are several posts there regarding this problem.

---

### Post by vancouverite on 2011-07-04
@lovinglinux:
Thanks for you help, but that thread is 101 pages long and using the search terms "connection refused" came up empty.  I'm having the same problem, and as much as I like browsing the forums, that's a lot of reading to address a [hopefully] simple problem.

Any other pointers would be much appreciated.

Van

---

### Post by lovinglinux on 2011-07-04
> **vancouverite said:**
> @lovinglinux:
Thanks for you help, but that thread is 101 pages long and using the search terms "connection refused" came up empty.  I'm having the same problem, and as much as I like browsing the forums, that's a lot of reading to address a [hopefully] simple problem.

Any other pointers would be much appreciated.

Van

If you are using the firewall, then probably it is blocking the port used to retrieve the key from the keyserver. Open up your Firewall.

---

### Post by vancouverite on 2011-07-05
Hi lovinglinux,
Thanks for the hint!  I'm behind a firewall that I don't have control over, but your tip lead me to this post:
[http://www.omgubuntu.co.uk/2011/01/how-to-add-repositories-to-ubuntu-from-behind-a-firewall/](http://www.omgubuntu.co.uk/2011/01/how-to-add-repositories-to-ubuntu-from-behind-a-firewall/)
which solved my problem.

Regards.

---

### Post by lovinglinux on 2011-07-05
> **vancouverite said:**
> Hi lovinglinux,
Thanks for the hint!  I'm behind a firewall that I don't have control over, but your tip lead me to this post:
[http://www.omgubuntu.co.uk/2011/01/how-to-add-repositories-to-ubuntu-from-behind-a-firewall/](http://www.omgubuntu.co.uk/2011/01/how-to-add-repositories-to-ubuntu-from-behind-a-firewall/)
which solved my problem.

Regards.

You are welcome.

BTW, in my first reply I just assumed the problem was with the server, but this particular issue is not covered in the Mega Thread.

---

