---
title: "Chromium Browser repositories?"
date: 2009-10-09
forum: General Help
---

### Post by xdemo on 2009-10-09
Hi there, i have recently installed/added the chromium repositories to apt-get


sudo apt-get update:
```
...
...
Fetched 140kB in 1s (101kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: You may want to run apt-get update to correct these problems
demo@jaunty:~$ 

```

When i followed a tutorial on adding the repositories to install it, i never encountered anything about adding public keys, which i can remember doing for another application a while back.

Chromium runs fine, except i want to remove this error. How do i assign / find the public key, and what are the commands to sign it?

Thank You.

---

### Post by MelDJ on 2009-10-09
does it come saying 'NO PUB KEY'? if it does, follow this: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by johny_ on 2009-10-09
I'd recommend you to remove all that new chrome repos entries you've manually put to the sources list
If you download Chromium from [here]("http://dev.chromium.org/getting-involved/dev-channel") (scroll down to "linux"), it will add the right Google repository by itself and manage the keys.

However, if you just want to find out on what's the whole thing is about, go [here]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding Other Repositories") and see the point called "authentication"

---

### Post by scorp123 on 2009-10-09
> **xdemo said:**
> NO_PUBKEY 5A9BF3BB4E5E17B5 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5


BTW, this line probably works too:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5

(it's the same key)

---

### Post by xdemo on 2009-10-09
Thanks for the replies people... this one fixed it:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5

```

Then followed by 
```
sudo aptitude udpate
```

Problem Solved :D

---

