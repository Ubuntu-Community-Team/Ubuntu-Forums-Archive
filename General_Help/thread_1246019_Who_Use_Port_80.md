---
title: "Who Use Port 80?"
date: 2009-08-21
forum: General Help
---

### Post by tanah.melayu on 2009-08-21
Yesterday, I did a test to use [HFS]("http://www.rejetto.com/hfs/") in my Ubuntu. [HFS]("http://www.rejetto.com/hfs/") is actually used on Windows.. we can simply run it to start a webserver without need to install Apache, Php and MySQL. I tried to run it through Wine. It works fine but I found something happened. HFS automatically detect port 8080 to set up the webserver rather than port 80 which it should choose. As I don't have Apache in my Ubuntu, does anyone knows; whatelse in Ubuntu use port 80 in default?

I found the same problem before in Windows but I realized that it was because of IIS. It worked fine after I removed IIS. However, in this case; I don';t have Apache installed and I think, there must be other program which is using port 80. Anyone knows? :P

---

### Post by credobyte on 2009-08-21
By default, 80 port is closed ( eg. not in use ).

Try:
```
netstat -a
```

Or, try nmap - works perfect :)

---

### Post by wojox on 2009-08-21
Try turning it off and edit the port box to 80 and turn it back on. It may default to 8080 because it's a file sharing server and not a web server.

---

### Post by tanah.melayu on 2009-08-21
> **credobyte said:**
> By default, 80 port is closed ( eg. not in use ).

Try:
```
netstat -a
```Or, try nmap - works perfect :)

i'll try this nite... :D

> **wojox said:**
> Try turning it off and edit the port box to 80 and turn it back on. It may default to 8080 because it's a file sharing server and not a web server.
I did but it still didn't work... :(

---

