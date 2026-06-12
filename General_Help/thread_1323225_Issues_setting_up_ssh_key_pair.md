---
title: "Issues setting up ssh key pair"
date: 2009-11-11
forum: General Help
---

### Post by Kennycl on 2009-11-11
Apologies for all these posts, I only starting using linux a few days ago so am having fun getting it all setup! (As a real plus the basic setup was very easy and my wife has even ditched windows for it in a couple of days!)

I'm trying to setup my home computer to mount my work hard drives using sshfs, there are several of them. I can manually mount them using sshfs no problem, other than I have to type my password in for each mount. I would like some way of avoiding this. I thought a key pair may work well as the likelihood of anyone getting physical access to either machine is small so I would have thought the key files are relatively secure. 

I have basically followed the tutorial at [http://ubuntuforums.org/showthread.php?t=238672](http://ubuntuforums.org/showthread.php?t=238672) but when I try to ssh to the remote host I get the error message Agent admitted failure to sign using the key.

Any ideas?

Thanks,

Kenny

---

### Post by spiderbatdad on 2009-11-11
so the work computer should run as the server (host), and your home computer is the client, remotely mounting the host file system. You want to generate the key pair on the host. Then copy id_rsa.pub to the client machine. So you need to ssh into the client, from work, as well or physically copy the key to some other medium (flash drive) and transfer to the appropriate folder at home.

---

### Post by Kennycl on 2009-11-11
Sorted, thanks!

---

