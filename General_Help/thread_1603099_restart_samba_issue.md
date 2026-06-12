---
title: "restart samba issue"
date: 2010-10-22
forum: General Help
---

### Post by dobby156 on 2010-10-22
Hi all.
I am currently following this guide:
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")

trying to connect my Ubuntu system to my domain, however that is not the problem. The guide instructs me to edit smb.conf file which I have done and check backing up the original to as smb.conf.backup in the same dir.

Now I need to restart samba, so I enter

> 
sudo /etc/init.d/samba restart


and I get command not found. 
I have tried start instead of restart, smb instead of samba, "service samba start" instead. all give more or less the same error.

I have restarted the system to no avail.

If I run "ps aux" there is no mention of smb or samba, although I aren't sure whether the is supposed to be, I image so.

I have also tried running apt-get install again to ensure it is installed and it just says I have the newest version.

The system is Ubunutu 10.10 SERVER running no other services, and is CLI only.

Thanks for your Help, I hope I provided enough information

---

### Post by blueridgedog on 2010-10-22
Try 

```
sudo service smb restart
```

---

### Post by sikander3786 on 2010-10-22
And for individual restarts/reloads/stops you can also use,

```
sudo service smbd start
```

```
sudo service nmbd start
```

---

### Post by doccpu on 2010-12-03
argh so frustrating. one manual/person says this one says that. How does samba in ubuntu 10.04 get restarted? no service commands work. No etc/init.d entries. so how DO you run samba in 10.04
? 
many say go to system/admin/services. well i would but that and severl other submenus everybody seems to think are there are not. like services, networking etc etc. Do people really use ubuntu out of the box or do they spend months getting it to work then expect it to be the same out of the box when they give support?

---

### Post by 3rdalbum on 2010-12-03
> **doccpu said:**
> argh so frustrating. one manual/person says this one says that. How does samba in ubuntu 10.04 get restarted? no service commands work. No etc/init.d entries. so how DO you run samba in 10.04
? 
many say go to system/admin/services. well i would but that and severl other submenus everybody seems to think are there are not. like services, networking etc etc. Do people really use ubuntu out of the box or do they spend months getting it to work then expect it to be the same out of the box when they give support?

Ubuntu has changed a lot. Only follow instructions from the correct version of Ubuntu, otherwise things may be different. The instructions you speak of are about 18 months old, at least which is why you can't follow them on Ubuntu 10.10.

---

