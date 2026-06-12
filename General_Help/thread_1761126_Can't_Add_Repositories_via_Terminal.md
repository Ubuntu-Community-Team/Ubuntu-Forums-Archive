---
title: "Can't Add Repositories via Terminal"
date: 2011-05-17
forum: General Help
---

### Post by xxhopingtearsxx on 2011-05-17
Everytime I do, I'm given an error message..

> joey@joey-ubuntu:~$ sudo add-apt-repository ppa:banshee-team/banshee-daily
[sudo] password for joey: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: public key "Launchpad PPA for Banshee Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
joey@joey-ubuntu:~$ sudo -s
root@joey-ubuntu:~# sudo add-apt-repository ppa:banshee-team/banshee-daily
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: "Launchpad PPA for Banshee Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@joey-ubuntu:~# 



---

### Post by xxhopingtearsxx on 2011-05-17
Bump.

---

### Post by spcwingo on 2011-05-17
Please post the output of this command:

```
ls /etc/apt/sources.list.d/ | grep banshee
```

This should show if you just need to run:

```
sudo apt-get update
```

or if something else is going on.

---

### Post by xxhopingtearsxx on 2011-05-17
I'm assuming it wasn't an error then..
seeing how I got:
banshee daily.. Unless that's not the one I wanted. I wanted to get the updates from [https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

```
joey@joey-ubuntu:~$ ls /etc/apt/sources.list.d/ | grep banshee
banshee-team-banshee-daily-natty.list
banshee-team-banshee-daily-natty.list.save
banshee-team-ppa-natty.list
banshee-team-ppa-natty.list.save
joey@joey-ubuntu:~$ 







```

---

### Post by spcwingo on 2011-05-17
It looks like it's there.  You might just need to run:

```
sudo apt-get update
```

After that, just update how you normally would or with:

```
sudo apt-get upgrade
```

---

### Post by athenroy on 2011-05-17
My problem is a little different and maybe I missed a post on it.  I run 11.04 with the classic desktop.  When I bring up a terminal and try the sudo apt-get method when I hit enter, the next line is "password for bill~$  When I try and enter my password, the keyboard is frozen and I can't enter anything.  Installation works fine from Synaptic package manager and the software center GUIs.  Just wondering what's up with my terminal. :confused:  Thanks for any help.

---

### Post by spcwingo on 2011-05-17
> **athenroy said:**
> My problem is a little different and maybe I missed a post on it.  I run 11.04 with the classic desktop.  When I bring up a terminal and try the sudo apt-get method when I hit enter, the next line is "password for bill~$  When I try and enter my password, the keyboard is frozen and I can't enter anything.  Installation works fine from Synaptic package manager and the software center GUIs.  Just wondering what's up with my terminal. :confused:  Thanks for any help.

You'll probably have to open a new thread on that one.  It sounds like a completely different issue.

---

