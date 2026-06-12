---
title: "Server 7.10 E:can't find package samba"
date: 2010-01-31
forum: General Help
---

### Post by wdr on 2010-01-31
I'm an Ubuntu novice. Setting up a simple file server with Server 7.1. All looks well except it will not let me install samba I get a "E: can't find samba package" error.  I can ping [www.google.com](www.google.com) and nodes on the LAN so I know I have signal out and in.

Ideas?
Thanks,
Will

---

### Post by wojox on 2010-01-31
You ran this command:

```
sudo apt-get install samba smbfs
```

---

### Post by t4thfavor on 2010-01-31
Is 7.10 in the repos still, I thought it would be EoL by now, perhaps this is why you cannot find the package.

---

### Post by wdr on 2010-01-31
> **wojox said:**
> You ran this command:

```
sudo apt-get install samba smbfs
```

That results in the "can't find package" error???????

---

### Post by wojox on 2010-01-31
> **t4thfavor said:**
> Is 7.10 in the repos still, I thought it would be EoL by now, perhaps this is why you cannot find the package.

That's right, I was thinking Ubuntu 8.04 LTS.

---

### Post by wdr on 2010-01-31
> **wojox said:**
> That's right, I was thinking Ubuntu 8.04 LTS.

Perhaps me should d/l the latest release.

---

### Post by wojox on 2010-01-31
Sounds like a plan. ;)

---

### Post by wdr on 2010-01-31
> **wojox said:**
> Sounds like a plan. ;)
What server release will run on a 233mhz PII Dual Processor box? 9.10 ain't gonna.

---

### Post by kmsalex on 2010-01-31
>  What server release will run on a 233mhz PII Dual Processor box? 9.10  ain't gonna.you could try xubuntu, i got 9.10 to run on a 267mhz with 128 mb ram(yes with the GUI) painfuly slow to boot, but not half bad once it got going. but you might want to wait for the next LTS in april as 8.04 is going to be droped when 10.04 comes out.

---

### Post by gmargo on 2010-02-01
You can still load packages for Gutsy 7.10, but since the release is no longer supported, you have to change your **/etc/apt/sources.list** file to point to [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/).

But since it is so old and no longer gets security updates, you'd be better off with a newer release.

---

