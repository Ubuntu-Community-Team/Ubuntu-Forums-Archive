---
title: "Fail during select best server (software source)"
date: 2010-04-12
forum: General Help
---

### Post by plusnplus on 2010-04-12
Hi,
I'm using ubuntu 9.04 desktop 64 bit.
I try to change software source, but always fail during process select best server.
The error mesasge is "no suitable download server was found. please check your internet connection."

in firefox, i can surft internet without any problem.

Thanks for any help.

---

### Post by plusnplus on 2010-04-13
Another info about my pc(server):
when i open firefox, I need to enter user name and password for my proxy server.
is that maybe why I can not do update/ install software?
Anyone know how to solve it?

---

### Post by plusnplus on 2010-04-13
I found similiar case at [http://www.linuxforums.org/forum/ubuntu-help/136436-help-no-suitable-server-found.html](http://www.linuxforums.org/forum/ubuntu-help/136436-help-no-suitable-server-found.html)

but not final solution. The helper said something about "it may just be a DNS resolution problem"

any idea what is that about ?

---

### Post by plusnplus on 2010-04-14
I found again similiar solution at [http://ubuntuforums.org/showthread.php?t=267868](http://ubuntuforums.org/showthread.php?t=267868)

what i did is type in terminal:
sudo gedit /etc/resolv.conf

and add:
nameserver 208.67.222.222 (change to your own ISP public DNS IP)
nameserver 208.67.220.220 (change to your own ISP public DNS IP)

after that i get result if i type:
host yahoo.com
or 
nslookup yahoo.com

but still i can not update/ install any software.

anyone can help?

---

### Post by plusnplus on 2010-04-14
Anyone can help me :)

---

### Post by plusnplus on 2010-04-15
Finaly .... i can solve the problem.
found the solution from:
[https://lists.ubuntu.com/archives/ubuntu-users/2005-September/048213.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-September/048213.html)

what i did is same, add:
ACQUIRE {
        http::proxy "http://user:password@proxy:8080/"
}

in /etc/apt/apt.conf file.

hope it helpfull to everyone who have same problem :)

---

