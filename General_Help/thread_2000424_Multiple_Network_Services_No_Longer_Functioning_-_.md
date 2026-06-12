---
title: "Multiple Network Services No Longer Functioning - 10.04.4"
date: 2012-06-09
forum: General Help
---

### Post by beardedman on 2012-06-09
Hello,

I'm running an ubuntu 10.04.4 x64 installation as a general purpose web server. It's primary functions are:
[LIST]
[*]Hosting websites with Apache
[*]Management of the server via SSH
[*]Local network media sharing (I have a second hard drive attached who's partition gets automounted at bootup)
[*]A minecraft server for my younger brother and his friends
[/LIST]

It wasn't until yesterday that I started having problems. None of the above services function anymore. The last thing I was trying to accomplish was to add ventrilo as an automatically started service.

I had the ventrilo software running, but could only connect by typing in the servers local ip address. Shortly thereafter, none of the other services functioned anymore. 

So I removed every trace of ventrilo that I could find:
[LIST]
[*]Deleted general files
[*]removed folders and startup scripts from /etc/init.d
[*]removed ventrilo related configurations from update-rc.d
[/LIST]

But the issue was still there so, I thought that perhaps I had unknowingly made some obscure change to my firewall (a pfSense box), so I wiped and reloaded the box. My computers are back online, but the services are still not accessible (even with the appropriate NAT rules). 

I've tried doing some research online, but the only thing I can find similar to my issue [involved commenting out a portion of a line in rc-sysinit.conf to prevent services from waiting on the loopback device to load prior to starting]("http://ubuntuforums.org/showthread.php?t=1393573"), which did not fix my problem.

On one final note, when I connect a monitor to the server and watch the bootup process, it does report that it starts the apache server and minecraft server ok.

The ubuntu installation is fairly new, roughly three weeks old,and I'd hate to have to reinstall.

I really appreciate any and all help that comes my way. Thank you!

*****Update*****
I have confirmed that the issue is with the Ubuntu server. I have installed apache on another box, altered my router/firewall's nat to the test box, and successfully browsed to my external ip through another computer.

---

### Post by beardedman on 2012-06-09
:redface: **smacks own head**, boy do I feel dumb...

I must have inadvertently added some firewall rules because after:

```
sudo ufw disable
```

everything magically started working.

---

