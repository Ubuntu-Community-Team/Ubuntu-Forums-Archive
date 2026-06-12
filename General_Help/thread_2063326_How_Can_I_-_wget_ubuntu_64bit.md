---
title: "How Can I - wget ubuntu 64bit"
date: 2012-09-26
forum: General Help
---

### Post by sdpagent on 2012-09-26
Dear all,
I am trying to get the ubuntu 12.04 server image on my centos server (no gui) before performing a virtual machine install in xen.

Whenever I run ```
wget http://www.ubuntu.com/start-download?distro=server&bits=64&release=lts
```I receive the following output before downloading the 32bit version:

```
[root@localhost ~]# wget http://www.ubuntu.com/start-download?distro=server&bits=64&release=lts
[1] 12235
[2] 12236
[root@localhost ~]# --2012-09-26 11:14:54--  http://www.ubuntu.com/start-download?distro=server
Resolving www.ubuntu.com... 91.189.90.40
Connecting to www.ubuntu.com|91.189.90.40|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://mirror.sov.uk.goscomb.net/ubuntu-releases//precise/ubuntu-12.04.1-server-i386.iso [following]
--2012-09-26 11:14:54--  http://mirror.sov.uk.goscomb.net/ubuntu-releases//precise/ubuntu-12.04.1-server-i386.iso
Resolving mirror.sov.uk.goscomb.net... 93.89.90.2, 2a01:348:0:11::aaaa
Connecting to mirror.sov.uk.goscomb.net|93.89.90.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 676638720 (645M) [application/x-iso9660-image]
Saving to: `ubuntu-12.04.1-server-i386.iso'
```Does anyone know a better way to retrieve the image directly with wget?

Stu

---

### Post by pompel9 on 2012-09-26
I know this may be a dumb question. But why do you not just download the iso from ubuntu homepage in your browser? 

It would be faster than getting an answer to your question.

Just a suggestion :)

Whoops, overlooked the no GUI bit. Never mind, just ignore my answer.

---

### Post by mikewhatever on 2012-09-26
Try this:

wget [http://releases.ubuntu.com/precise/ubuntu-12.04.1-server-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04.1-server-amd64.iso)

---

### Post by llamabr on 2012-09-26
Of course, you don't need a gui to load a web site or a web browser.  Try w3m, links, or lynx.

---

### Post by sdpagent on 2012-09-26
> **mikewhatever said:**
> Try this:

wget [http://releases.ubuntu.com/precise/ubuntu-12.04.1-server-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04.1-server-amd64.iso)

Thank you this proved to be what I wanted. 

With regards to the 'just download in browser' comment someone else made, I have never used a 'text/console browser' before, maybe this is something I should look into.

Thanks again everyone.
Stu

---

