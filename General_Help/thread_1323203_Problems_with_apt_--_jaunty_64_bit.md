---
title: "Problems with apt -- jaunty 64 bit"
date: 2009-11-11
forum: General Help
---

### Post by lesswatts on 2009-11-11
I have several problems, I would assume they come from the same source.  This is occurring on a vps that was imaged yesterday, I have not made any modifications to any config files (other than apache2)

when running ```
apt-get update
```several messages like this are displayed:
```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages.bz2  Waited for bzip
2 but it wasn't there
```When running an ```
apt-get install irssi
``` this error is returned:

```
x@bean:~$ sudo apt-get install irssi                                                                                
Reading package lists... Done                                                                                           
Building dependency tree                                                                                                
Reading state information... Done                                                                                       
Suggested packages:                                                                                                     
  irssi-scripts                                                                                                         
The following NEW packages will be installed:                                                                           
  irssi                                                                                                                 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.                                                          
Need to get 0B/1165kB of archives.                                                                                      
After this operation, 3084kB of additional disk space will be used.                                                     
E: Waited for /usr/sbin/dpkg-preconfigure --apt || true but it wasn't there                                             
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true 
```I have tried running ```
dpkg-reconfigure -a
``` but that did not seem to help.

Any ideas?

---

### Post by tuwe on 2009-11-11
i wonder if you accidentally uninstalled bzip2 and dpkg-preconfigure. What is the output of ```
which bzip2
which dpkg-preconfigure
``` ?

edit: maybe useful as well: ```
echo $PATH
```

---

### Post by lesswatts on 2009-11-11
> **tuwe said:**
> i wonder if you accidentally uninstalled bzip2 and dpkg-preconfigure. What is the output of ```
which bzip2
which dpkg-preconfigure
``` ?

edit: maybe useful as well: ```
echo $PATH
```


here is the first output:
```
root@bean:~# which bzip2
/bin/bzip2
root@bean:~# which dpkg-preconfigure
/usr/sbin/dpkg-preconfigure
root@bean:~#

```and the second:

```
root@bean:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by lesswatts on 2009-11-11
I just tried running the commands that were giving me problems again, after getting the output of those commands, and it worked without a problem... the server was not rebooted.

However, when attempting to run (the now newly installed) irssi I recieve this error:

```
Can't open /dev/null: Permission denied
Segmentation fault
``` What is going on here?

---

