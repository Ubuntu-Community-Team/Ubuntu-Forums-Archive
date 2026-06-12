---
title: "Failed to install mysql on Ubuntu 10.04"
date: 2010-05-04
forum: General Help
---

### Post by mengruojun on 2010-05-04
Hello. Today I installed Ubuntu 10.04 and plan to install mysql server on it.
I use the following command,but it failed:
```
sudo apt-get install mysql-server-5.1
```

I realized the system would need to be update, then I use this command both in Synaptic Manager and terminal:
```
sudo apt-get update
```
But it returned a error:
```
W: Failed to fetch http://cn.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

```


I guess maybe the source URL is invalid but I have no idea how to resolve it.

If someone can give me a hand? Thank!

---

### Post by Seal Daemon on 2010-05-04
Have you tried to change the server ?

---

### Post by mengruojun on 2010-05-04
> **Seal Daemon said:**
> Have you tried to change the server ?

That is the question. How to change? Thanks.

---

### Post by qhaz on 2010-05-04
> **mengruojun said:**
> That is the question. How to change? Thanks.
mengruojun to change to a different server you need to start update manager first.  System > Administration > Update Manager.
Then after entering your password, click on the "settings" button (bottom left).
Then click on the "Ubuntu Software" tab.
You'll see there a drop-down menu next to "Download From" where you can choose a different server to download from.

Cheers

---

### Post by svabhishek on 2010-05-04
> **mengruojun said:**
> Hello. Today I installed Ubuntu 10.04 and plan to install mysql server on it.
I used the following command,but it failed:
```
sudo apt-get install mysql-server-5.1
```I realized the system would need to be update, then I use this command both in Synaptic Manager and terminal:
```
sudo apt-get update
```But it returned a error:
```
W: Failed to fetch http://cn.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2  Hash Sum mismatch
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
I guess maybe the source URL is invalid but I have no idea how to resolve it.

If someone can give me a hand? Thank!


hm.. actually i tried installing it using the same command and MySQL was  installed perfectly and I am also using Drupal over that .. so it means  there is nothing wrong with the server or the link

---

