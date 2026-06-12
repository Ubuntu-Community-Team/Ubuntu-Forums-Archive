---
title: "/dev/ttyUSB* is getting locked"
date: 2010-02-08
forum: General Help
---

### Post by shariefbe on 2010-02-08
Hello,
  I am using Ubuntu 9.10.When ever i tri minicom i am getting error message as 
```

Device /dev/ttyUSB0 is locked.
sharief@sharief-desktop:~$ 
```
I searched in /var/lock/ file. Nothing in that.
```

sharief@sharief-desktop:/var/lock$ ls
sharief@sharief-desktop:/var/lock$ 

```
then i searched /var/tmp/. No file related to ttyUSB*.
```

sharief@sharief-desktop:/var/tmp$ ls
motd.tail.swp
sharief@sharief-desktop:/var/tmp$ 

```
i searched in /tmp/ also. I didnt found any thing related to ttyUSB*
```

sharief@sharief-desktop:/tmp$ ls
keyring-gh9KXe  orbit-sharief  pulse-PKdhtXMmr18n  pulse-z0Fis1zFYvrJ  seahorse-OZ5gwy  ssh-FtAuvo3036  virtual-sharief.Vcp4dL
sharief@sharief-desktop:/tmp$ 

```
So please help me. what will be the problem. Sometimes it is working but after sometime it is getting locked. Please help me

---

