---
title: "How to target machine via hostname?"
date: 2009-10-01
forum: General Help
---

### Post by TheOrangePeanut on 2009-10-01
When I want to ssh into a machine on my local network, I have to do so with the ip address ala ssh name@192.168.1.101.  I'd like to be able to do it by doing ssh name@hostname and that be the end of it, but it doesn't work like that and I'm not sure how to set it up.

I ask because I also need to do other things, like open shared directories in a file browser (such as file:///hostname/path/to/folder for example).  I can do this on my Windows machines, so surely there is a way to do it on my Linux boxes as well.

---

### Post by louieb on 2009-10-01
The way I do it on my home network.
using my routers configuration assign each pc its IP - router then assigns IP based on the computers MAC id. 
then add a line to /etc/hosts for each pc on the network.
```

lou@lou-laptop:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    lou-laptop
10.0.0.3 blackbox
10.0.0.5 playbox
10.0.0.6 barbtop
10.0.0.7 whitebox
10.0.0.13 loutop 

```

Works alright for a small network. Probably would be a pain on a larger metwork.

---

