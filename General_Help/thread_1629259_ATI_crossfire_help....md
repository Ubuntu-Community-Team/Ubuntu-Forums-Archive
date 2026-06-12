---
title: "ATI crossfire help..."
date: 2010-11-23
forum: General Help
---

### Post by Edgeraven on 2010-11-23
Hi, I am running Ununtu 10.10 64 bit and I noticed while playing a game that only one of my graphics cards is working. I have two radeon hd 3870 toxic 512 mb graphics cards. So I am trying to get crossfire to work...I have tried running an install but this is what I get...
edgeraven@edgeraven-MS-7376:~$ sudo apt-get install crossfire-client-gtk2 crossfire-client-images crossfire-client
[sudo] password for edgeraven: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
edgeraven@edgeraven-MS-7376:~$

Any help would be awesome and thank you in advance...

---

### Post by dankdank on 2010-12-23
Try this

```
sudo killall apt-get
```

If that doesn't work try

```
sudo killall aptitude
```

That solved my problem when I got that "lock" error

---

