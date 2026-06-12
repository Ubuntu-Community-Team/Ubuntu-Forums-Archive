---
title: "apt-get issue"
date: 2011-05-07
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2011-05-07
Hi, recently sudo apt-get update (and all other apt-get commands) has resulted in the error:

> apt-get: command not found

I have apt installed, and I don't know of any changes I've made (I booted a Freebsd install dvd but I didn't end up installing (i'm looking at putting it onto an external hdd). 

I've googled the issue and not found a solution. 

Output of sudo find / -name "apt-get" -print:

> /usr/bin/apt-get

Output of apt- (+ tab tab)
> 
apt-add-repository    apt-config            apt-key
apt-cache             apt-extracttemplates  apt-mark
apt-cdrom             apt-ftparchive        apt-sortpkgs


Output of ls /usr/bin/apt*

> /usr/bin/apt-add-repository    /usr/bin/aptitude
/usr/bin/apt-cache             /usr/bin/aptitude-create-state-bundle
/usr/bin/apt-cdrom             /usr/bin/aptitude-run-state-bundle
/usr/bin/apt-config            /usr/bin/apt-key
/usr/bin/aptdcon               /usr/bin/apt-mark
/usr/bin/apt-extracttemplates  /usr/bin/apt-sortpkgs
/usr/bin/apt-ftparchive        /usr/bin/apturl
/usr/bin/apt-get               /usr/bin/apturl-gtk


/usr/bin/apt-get in the last output is normal lightgreen (my terminal txt colour) but the other options are bold dark green (except apt-add-repository which is blue).

I still seem to be able to install/update from update manager and synaptic, but I rely on command line for apt-get update when I'm not at uni (which runs through a proxy).

Any help would be greatly appreciated. Thanks in advance.

---

### Post by matt_symes on 2011-05-07
Hi

What is the output of these commands

```
ls -l /usr/bin/apt*
```

Thats a small L after ls.

```
echo $PATH
```

```
file /usr/bin/apt-get
```

```
which apt-get
```

```
sudo /usr/bin/apt-get update
```

Kind regards

---

### Post by Dalek Draco ON LINUX on 2011-05-07
Hi, outputs are:

> draco@draco-laptop:~$ sudo ls -l /usr/bin/apt*
lrwxrwxrwx 1 root root      18 2010-11-19 15:16 /usr/bin/apt-add-repository -> add-apt-repository
-rwxr-xr-x 1 root root   64504 2011-02-24 07:20 /usr/bin/apt-cache
-rwxr-xr-x 1 root root   23136 2011-02-24 07:20 /usr/bin/apt-cdrom
-rwxr-xr-x 1 root root   14800 2011-02-24 07:20 /usr/bin/apt-config
-rwxr-xr-x 1 root root    1038 2010-08-25 16:29 /usr/bin/aptdcon
-rwxr-xr-x 1 root root   27352 2011-02-24 07:20 /usr/bin/apt-extracttemplates
-rwxr-xr-x 1 root root  180064 2011-02-24 07:20 /usr/bin/apt-ftparchive
---------- 1 root root  122640 2011-02-24 07:20 /usr/bin/apt-get
-rwxr-xr-x 1 root root 2270504 2010-04-09 22:41 /usr/bin/aptitude
-rwxr-xr-x 1 root root    1939 2010-04-09 22:41 /usr/bin/aptitude-create-state-bundle
-rwxr-xr-x 1 root root    3007 2010-04-09 22:41 /usr/bin/aptitude-run-state-bundle
-rwxr-xr-x 1 root root    6521 2011-02-24 07:20 /usr/bin/apt-key
-rwxr-xr-x 1 root root    3253 2011-02-24 07:20 /usr/bin/apt-mark
-rwxr-xr-x 1 root root   27176 2011-02-24 07:20 /usr/bin/apt-sortpkgs
-rwxr-xr-x 1 root root     273 2010-03-15 17:37 /usr/bin/apturl
-rwxr-xr-x 1 root root    1547 2010-03-20 01:51 /usr/bin/apturl-gtk


> draco@draco-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

> draco@draco-laptop:~$ file /usr/bin/apt-get
/usr/bin/apt-get: regular file, no read permission

> 
draco@draco-laptop:~$ which apt-get
draco@draco-laptop:~$

> draco@draco-laptop:~$ sudo /usr/bin/apt-get update
[sudo] password for draco: 
sudo: /usr/bin/apt-get: command not found


---

### Post by matt_symes on 2011-05-07
Hi

> ---------- 1 root root 122640 2011-02-24 07:20 /usr/bin/apt-get

How on earth did that happen ?

Try this.

```
sudo chmod 751 /usr/bin/apt-get
```

then

```
sudo apt-get update
```

Kind regards

---

### Post by Dalek Draco ON LINUX on 2011-05-07
Thank you that worked!  Slightly nooby question..what was the problem? chmod 751 changes file permissions according to my google search....so I had incorrect file permissions?  I installed and ran Bastille a few weeks ago, but I'm pretty sure I've been using apt-get from terminal since then, so I don't think that would have caused it.   Either way thanks again :D

---

### Post by matt_symes on 2011-05-07
Hi

> so I had incorrect file permissions?

Yes. apt-get had no read, write or executable permission for anybody on your pc including root.

Kind regards

---

### Post by Dalek Draco ON LINUX on 2011-06-14
Sorry to revive the thread months later, but I've just had the same problem, fixed it the same way. 

Any idea how I would go about finding out what is causing it to change the permissions?

---

### Post by matt_symes on 2011-06-15
Hi

Is it happening after an update to apt ? 

I have just ran apt-get upgrade and it updated the package apt.

What does this return.

```
grep "status installed apt" /var/log/dpkg.log
```

check the dates against when it stopped working.

Kind regards

---

### Post by Dalek Draco ON LINUX on 2011-07-22
It hasn't stopped working for a while, but the last update I did (today, to apt) caused it to happen again. I ran the fix and it works again. output of that is:

grep "status installed apt" /var/log/dpkg.log 
2011-07-22 14:40:09 status installed apt 0.7.25.3ubuntu9.6
2011-07-22 14:40:15 status installed apt-utils 0.7.25.3ubuntu9.6
2011-07-22 14:40:15 status installed apt-transport-https 0.7.25.3ubuntu9.6

---

