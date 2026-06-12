---
title: "get-apt install issue"
date: 2009-10-07
forum: General Help
---

### Post by rsvr85 on 2009-10-07
Hey UbuntuForums!

I'm new to the forum & to Linux/Ubuntu, i switched from Windows nearly a week ago and so far i haven't looked back :D  I'm very excited about Linux and look forward to my stay here.

Anyways, I'm having a problem with; 

```
sudo apt-get update
```When i run it, i get the following error;

[B]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems[/B]


So, i try and run this;

```
gpg --keyserver keyserver.ubuntu.com --recv BF810CD5

```I then get this output

[B]gpg: WARNING: unsafe permissions on configuration file `/home/stuart/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/stuart/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
[/B] (If i run as sudo i get the same output apart from the first warning)

This is where i get stuck,
```
ls -l ~/.gnupg/gpg.conf
```Gives this output;
**-rwxrwx--x 1 root root 9508 2009-10-03 16:06 /home/stuart/.gnupg/gpg.conf**

and
```
ls -l ~/.gnupg/
```Gives this;
[B]-rwxrwx--x 1 root   root   9508 2009-10-03 16:06 gpg.conf
-rw------- 1 root   root      0 2009-10-04 02:52 pubring.gpg
-rw-rw---- 1 stuart stuart  600 2009-10-04 03:14 random_seed
-rw-rw---- 1 stuart stuart    0 2009-10-04 03:11 secring.gpg
-rw------- 1 root   root     40 2009-10-04 02:52 trustdb.gpg
[/B]

It's looks clear that the permissions of **gpg.conf** need changing but i have no idea how assign them correctly.  It's got something to do with chmod right???

Please be gentle [-o<,  As i say, i've only been using Ubuntu for 4 days now so all of this is super alien to me.

---

### Post by MelDJ on 2009-10-08
try this: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by rsvr85 on 2009-10-08
> **MelDJ said:**
> try this: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

That link you gave didn't work exactly according the the vid.  However, i have got it working after watching it.  Thanks for your help and the warm welcome MelDJ :D

---

### Post by MelDJ on 2009-10-08
its my pleasure. please mark the thread as solved

---

