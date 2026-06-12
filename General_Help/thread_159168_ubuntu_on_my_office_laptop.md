---
title: "ubuntu on my office laptop"
date: 2006-04-12
forum: General Help
---

### Post by hegenious on 2006-04-12
Hi,

after running breezy for about 5 months on my home desktop system with full satisfaction and having lots of fun tweaking ubu to do what I want it to do, I decided yesterday night to slam breezy on my company dell latitude laptop.

I'm a monitoring/automation guy for a big IT business in NL and basically that means doing remote mangement/ and tech support thru IBM Tivoli software, a lot on AIX, a bit HP-UX and a few SUN too. So I'm pretty familiar with unix.


Well yesterday I installed breezy as a dual boot with xp, which is the standard work environment that is company installed on my latitude. All went well and I was impressed with the partitoning tool that was able to resize my windows partition without having to tamper with partition magic. The wireless detection went flawless. This morning at work I excitedly fired up my ubuntu partition and wanted to have it do what I am used to do from my xp working env.

And here's where I could use some tips from you guys :]] I have some questions.

I need to connect to a company ms exchange server, can I do that with evolution?
At work I am connected through a private proxy to the internet, which means that I cannot connect to the ubuntu repositories from the office. What can be done about that? Can apt be configured to use the proxy?

Is there a RDP client for ubuntu that lets me connect to a windows 2000 terminal services? I really need that because most of the tooling that i use every day is on an app server w/ w2k remote desktop services.

And finally: I have a very nice dell 17" display that I'd like to hookup to the vga of my latitude as a dual head with extended desktop, just as i have with xp.
The hardware supports it, but how about ubuntu?

Well that is about it for now. Any help is appreciated.

Bye

---

### Post by evilregis on 2006-04-12
I've used Ubuntu at work and I can say that it is certainly capable of connecting to Windows terminal servers.  I'm not in Ubuntu right now because I'm having serious networking problems so I can't tell you exactly where it's at, but check in Applications -> Internet -> Terminal Services or something like that.  I believe its icon was a Windows logo inside a terminal screen or something similar.

---

### Post by Al3xanR0 on 2006-04-12
> **hegenious]I need to connect to a company ms exchange server, can I do that with evolution?[/QUOTE]

Yes -you will need the exchange plugin

[QUOTE=hegenious]At work I am connected through a private proxy to the internet, which means that I cannot connect to the ubuntu repositories from the office. What can be done about that? Can apt be configured to use the proxy?[/QUOTE]

Yes-you will need to add the following to you /etc/apt/apt.conf
```
ACQUIRE {
    Retries "3" said:**
> Is there a RDP client for ubuntu that lets me connect to a windows 2000 terminal services? I really need that because most of the tooling that i use every day is on an app server w/ w2k remote desktop services.

Yes- you will need to ```
apt-get install rdesktop
```
then  ```
rdesktop -a 24bpp -g 1010x645 -x l -r sound:remote <hostname>:3389
``` g= geometry adjust as desired..

[QUOTE=hegenious]And finally: I have a very nice dell 17" display that I'd like to hookup to the vga of my latitude as a dual head with extended desktop, just as i have with xp.
The hardware supports it, but how about ubuntu?[/QUOTE]

check the FAQ

---

### Post by hegenious on 2006-04-12
Thank you so much for all your kind responses.

looks like I'm in luck for most part I want  :D 

Found out that evolution comes with a full blown manual, gonna have to read it heheh. ](*,)

---

### Post by lamego on 2006-04-12
If you want to install the packages from the gui (Synaptic), you can also do the proxy configuration on the network settings. If the proxy requires authentaction you will need to use [http://user:pass@host:port](http://user:pass@host:port) on the proxy name.

---

### Post by Padre on 2006-04-14
Hi,
but if I need autorization by domain (for example domain\userid:password@proxy) gui not worked](*,)

---

### Post by Mr Fat Bat on 2006-05-10
The proxy should work with a domain.

My proxy looks (kind of) like this

ACQUIRE {
    Http {
        Proxy "http://some_domain\fatbat:passwd@proxy.addr.com:8080";
    }
};

---

