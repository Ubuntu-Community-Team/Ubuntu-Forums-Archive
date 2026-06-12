---
title: "ping a port"
date: 2009-08-11
forum: General Help
---

### Post by premabodh on 2009-08-11
Hi,

Is there a way to test if certain port is alive on the syatem. I wat to periodically ping port 8082 of my system.

Thanks,
Vikash Anand.
:popcorn:

---

### Post by TuckLive on 2009-08-11
```
sudo netstat -tpan
```

This will show you all listening ports on your system.

---

### Post by Brandon Williams on 2009-08-11
Netstat as TuckLive said if you're checking on the machine where the port should be listening.

If you're on another machine and want to check for tcp port liveness, you can install hping2.

---

### Post by credobyte on 2009-08-11
[http://www.canyouseeme.org]("http://www.canyouseeme.org/") does it's job very well.[URL="http://www.canyouseeme.org/"]
[/URL]

---

### Post by bear24rw on 2009-08-11
sudo aptitude install nmap

---

### Post by SlugSlug on 2009-08-11
> **premabodh said:**
> Hi,

Is there a way to test if certain port is alive on the syatem. I wat to periodically ping port 8082 of my system.

Thanks,
Vikash Anand.
:popcorn:


to test port 8082 on your machine from a remote location (say work)  easest way is use telnet...

telnet ip.address 8082

---

### Post by fragos on 2009-08-11
You can also use the GUI for this purpose. System-> Administration-> Network Tools. You have tab access to numerous tools including Port Scan.

---

