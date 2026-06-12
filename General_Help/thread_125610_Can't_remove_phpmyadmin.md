---
title: "Can't remove phpmyadmin"
date: 2006-02-04
forum: General Help
---

### Post by s_g_robertson on 2006-02-04
I am trying to install phpmyadmin on a new install of ubuntu.  I installed this on my laptop with no problems.

Everything seems to install okay and of i go to localhost in firefox then then i get my default apace directory or the phpmyadmin directory.  If i click on the phpmyadmin directory then firefox tries to download a phtml file.  I've made some changes to httpd.conf as a result of what I have found in the forums but nothing seems to help so I decided to uninstall phpmyadmin and apache and start again.

But I cant remove phpmyadmin.  this is what i get
```
stephen@ubuntu:~$ sudo apt-get remove phpmyadmin
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 61900 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
stephen@ubuntu:~$

```

Any suggestions?

Thanks

Stephen

---

### Post by Bongzilla on 2006-02-04
I have a similiar problem with lilypond, at least the error is almost identical. I hope someone could answer this. 

[http://ubuntuforums.org/showthread.php?t=125540](http://ubuntuforums.org/showthread.php?t=125540)

---

### Post by cutOff on 2006-02-04
Hi there

Edit the file /var/lib/dpkg/info/phpmyadmin.prerm and add the following behind "# Package maintainer's commands follow:" 

> . /usr/share/debconf/confmodule

Now you can do

```
sudo apt-get remove phpmyinstall
```

Hope it helps

---

### Post by lhtown on 2006-02-06
I was having exactly the same problem. I just added in the line you said right below the line "# Package maintainer's commands follow:" I saved it and it didn't work. I tried it again later and it worked like a charm. I must have done something wrong the first time like not saving it properly.

Thanks

---

### Post by s_g_robertson on 2006-02-10
[QUOTE=cutOff]Hi there

Edit the file /var/lib/dpkg/info/phpmyadmin.prerm and add the following behind "# Package maintainer's commands follow:" 



Now you can do

```
sudo apt-get remove phpmyinstall
```

Hope it helps[/QUOTE]

Thanks for that.  Unfortunately I don't know whether it solved my problem or not.  A few things seemed to have gone a bit weird and as it was an almost brand new install, I just started again.  I think the problem may have been down to issues when I was trying to install phpmyadmin in the first place.

Stephen.

---

### Post by EstevaoSoares on 2006-02-10
[QUOTE=cutOff]Hi there

Edit the file /var/lib/dpkg/info/phpmyadmin.prerm and add the following behind "# Package maintainer's commands follow:" 



Now you can do

```
sudo apt-get remove phpmyinstall
```

Hope it helps[/QUOTE]


Hey man, thanks a lot... 
Save me some pain :D

---

### Post by Heliix on 2006-06-26
wow.. it worked, thanks a lot :-)
editing the file & apt-get remove phpmyadmin just went smoothly :-)

---

