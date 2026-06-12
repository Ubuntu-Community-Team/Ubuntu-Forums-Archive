---
title: "Can't install &quot;build-essential&quot; on Ubuntu Server 8.10"
date: 2012-04-19
forum: General Help
---

### Post by kev670q on 2012-04-19
when I use    sudo apt-get update   all the pages that Ubuntu tries to get the resources from give 404 errors. I'm guessing this is because 8.10 is out of date but unfortunately I have to use it for other reasons. Can anyone tell me a work around of how I might do this with the older edition. I want to install gcc on the machine. Thanks...

---

### Post by dcstar on 2012-04-19
> **kev670q said:**
> when I use    sudo apt-get update   all the pages that Ubuntu tries to get the resources from give 404 errors. I'm guessing this is because 8.10 is out of date but unfortunately I have to use it for other reasons. Can anyone tell me a work around of how I might do this with the older edition. I want to install gcc on the machine. Thanks...

There are no active repositories for unsupported versions.

You may find the old packages here: [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

and set up the repositories like this: [http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty](http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty)

---

### Post by Cheesemill on 2012-04-19
Edit /etc/apt/sources.list and change it so only the following lines are present:
```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
```Then run:
```
sudo apt-get update
```Be aware that as 8.10 is no longer supported the packages may have bugs and security flaws that will never get patched.

---

### Post by iponeverything on 2012-04-19
posted to the wrong thread

---

### Post by kev670q on 2012-04-19
> **Cheesemill said:**
> Edit /etc/apt/sources.list and change it so only the following lines are present:
```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
```Then run:
```
sudo apt-get update
```Be aware that as 8.10 is no longer supported the packages may have bugs and security flaws that will never get patched.

Thanks a lot, Your solution worked perfectly...

also used this afterwards to install gcc and check that it was installed for anyone else who comes across this thread with google...

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
gcc --version
```


Sorry font police... Didn't know what thread to put it in...

---

### Post by dcstar on 2012-04-20
> **kev670q said:**
> Thanks a lot, Your solution worked perfectly...
.........

Then **mark** the thread.

---

