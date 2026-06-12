---
title: "Proxy problems"
date: 2006-02-28
forum: General Help
---

### Post by jofre on 2006-02-28
Hi lads, I have been working for a couple of days in a new job and the proxy setup is making me mad!

I can browse the net, and setup my email clients, but I can't manage to get "apt-get" to work.  The funny thing is that I manage to get working Synaptic (in theory just a GUI for apt-get, isn't it?), by putting in "Settings-->Preferences-->Networking: Manual proxy configuration: HTTP proxy: proxy.dcu.ie Port: 8080

I tried to follow the instruction from the Automatix thread (to make Automatix work with a proxy) but no luck.

My network administrator is not very familiar with linux. The most I could get out of him was:
jofre@edoras:~$ nslookup proxy.dcu.ie
Server:         136.206.20.3
Address:        136.206.20.3#53

Non-authoritative answer:
Name:   proxy.dcu.ie
Address: 136.206.1.20
Name:   proxy.dcu.ie
Address: 136.206.1.17

I tried then to put this in  /etc/apt/apt.conf

 ACQUIRE {
http::proxy"http://136.206.1.20:8080/"
} 

and actulally all the IP address showed above and when I try apt-get:

jofre@edoras:~$ sudo apt-get update
66% [Connecting to gb.archive.ubuntu.com]

and nothing else happen and i have to ctr+C to kill it.

Any help would be pretty much appreciated!

Thank, Jofre.

---

### Post by arnieboy on 2006-02-28
ok do this:
```
sudo gedit /etc/apt/apt.conf
```

and paste the following:
> ACQUIRE {
http::proxy "http://proxy.dcu.ie:8080/"
}

watch the blank between **proxy** and **"http...**
now do 
```
sudo gedit /etc/wgetrc
```

and find the following lines:
> # You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
#http_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)
#ftp_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)

# If you do not want to use proxy at all, set this to off.
#use_proxy = on

make them look as follows:

> # You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://proxy.dcu.ie:8080/](http://proxy.dcu.ie:8080/)
ftp_proxy = [http://proxy.dcu.ie:8080/](http://proxy.dcu.ie:8080/)
# If you do not want to use proxy at all, set this to off.
use_proxy = on

---

### Post by jofre on 2006-03-01
I CAN'T BELIEVE IT!!!!!!!!!!!!

Sorry for shouting: I can't believe it!!!!!!!!!!!!

Just a space!!! two days lost for just a blank space!!! :cry: :cry: 


Thanks a million Arnieboy!

---

