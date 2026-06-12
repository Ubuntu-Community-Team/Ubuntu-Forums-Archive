---
title: "Making a FTP server"
date: 2009-10-14
forum: General Help
---

### Post by TheStroj on 2009-10-14
Hi everyone!

I'm trying to set up a simple FTP server, so it would look something like this: [ftp://ftp.scv.si/vss/srecko_zorman/Gradiva/PRO1/](ftp://ftp.scv.si/vss/srecko_zorman/Gradiva/PRO1/)

That's all I need. Just one click and the file starts to download.

I'm not new to Ubuntu and not to terminal, but I'm new to internet stuff, so please explain it as easy as possible.
----

At home, we have a router, which is connected to modem. There are 3 computers connected to router: my desktop & laptop and my fathers computer. There are no computers connected directly to modem.
If I check my IP, it says: 192.168.2.101
(I guess that's not my real IP) - don't even know if this stuff is important, but I wrote it to make sure you have all the information needed.

There's also my 'ifconfig' output:
```

jure@jure-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:1c:29:14  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe1c:2914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20960 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:22683056 (22.6 MB)  TX bytes:2713509 (2.7 MB)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3049 (3.0 KB)  TX bytes:3049 (3.0 KB)

```

---

I want my server to be configured like this:

- I would be admin and there would be no other users other than me and everyone could download files from it (but ONLY DOWNLOAD, NOT upload)
- I want to make this look really simple on my computer, by making a folder where all the uploaded files would be (something like folder 'Files' with 'text.txt' in it and that file would be accessible to all people connecting to my site)

--- 

That's all I want =).
If there's a lot of things to do, I'll do them all. If you have any cool links, you can paste them here, but PLEASE, don't only paste links, try to help yourself (a complete guide to all I want to do would be amazing). 
I don't care if I have to use terminal or some good looking application - as long as it works, it's great!
If there are any questions, I'll try to answer!

---

### Post by nikhilbhardwaj on 2009-10-14
proftpd is what you are looking for

[http://news.softpedia.com/news/ProFTPD-Installation-Guide-36440.shtml](http://news.softpedia.com/news/ProFTPD-Installation-Guide-36440.shtml)

another guide may be found at
[http://www.proftpd.org/docs/](http://www.proftpd.org/docs/)

---

### Post by khelben1979 on 2009-10-14
Personally I would recommend [Pure-FTPd]("http://www.pureftpd.org/project/pure-ftpd"). Even I managed to set up my ftp server and I must admit that I'm no expert on this.

It's pretty fast as well.

---

