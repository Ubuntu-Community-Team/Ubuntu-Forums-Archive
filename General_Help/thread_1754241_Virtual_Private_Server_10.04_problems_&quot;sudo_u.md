---
title: "Virtual Private Server 10.04 problems &quot;sudo: unable to resolve host&quot;"
date: 2011-05-09
forum: General Help
---

### Post by scollum on 2011-05-09
After setting up a new VPS i can not install anything with apt-get or download anything with wget. 
on "sudo apt-get update" the output is
"sudo: unable to resolve host ovz.dltx.123systems.net"

on wget it is unable to resolve host of the address that the file resides. A clean install does not fix this. I am using Putty and a console applet provided by the 123systems. Problem persists in CentOS. 

What should i do?
Thanks in advance.

---

### Post by TheNerdAL on 2011-05-09
Maybe this thread might be of help: [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by scollum on 2011-05-09
For the host name and domain what should i use? i have found thread like that but i do not know what i should put for my set up. Is there some way i can find this out?

---

### Post by mrsmartstuff on 2011-07-13
this is what worked for me

On a freshly installed vps hosts looked like this.

```
127.0.0.1               localhost.localdomain localhost

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

I changed it to this after a little trial/error where soup was my server name

```
127.0.0.1               localhost
127.0.1.1               soup

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

