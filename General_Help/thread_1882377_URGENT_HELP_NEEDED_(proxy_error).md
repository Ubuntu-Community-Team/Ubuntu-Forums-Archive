---
title: "URGENT HELP NEEDED (proxy error)"
date: 2011-11-17
forum: General Help
---

### Post by richieza on 2011-11-17
Hi all, 

I need some serious help PLEASE!!!!!!
Im running Ubuntu 11.04 and somehow have messed up the global variables for proxy/network settings… 

At home have internet no proxy.
At varsity have internet but is proxy based (linux system have username and password) user = rich password = ieza, server is [http://www.xx.xxx.xx/xxxx.xxx](http://www.xx.xxx.xx/xxxx.xxx) (port 8080 i hope)


FIRSTLY I needed to disable proxy so I can work at home on the internet…. 
Have tried changing web browsers settings +

tried system->prefernces->network proxy->direct internet connection apply system wide & not system wide +

a few other things including changing the /etc/apt/apt.conf WHICH doesn’t exist on my Ubuntu 11.04) and also no mention of proxy in the bash.bashrc file SO don’t know wat to do here!!!


Secondly if I can restore my proxy to “direct internet connection” I would like to also be able to update packages at varsity (after changing the settings from no proxy at home to proxy for varsity)

Have tried changing proxy settings system->prefernces->network proxy-> to
Rich:ieza@http://www.xxxxx:8080
[http://Rich:ieza@www.xxxxx:8080](http://Rich:ieza@www.xxxxx:8080)

tried
apt.conf file as : Acquire::http: proxy (created this file did not previously exist!!)


ETC

Basically windows 7,xp works 100% can update software etc linux not being very friendly ATM..


THANKS A LOT!


//duplicated post... NEED HELP ASAP!!!!!!!!!!!!!!

---

### Post by ballantony on 2011-11-17
I have this exact same problem at home and work.  The big problem I have is authenticating against a windows proxy at work.  I can see the internet via firefox at work if I change the proxy settings, I need to use NTLMAPS to authenticate through the proxy to use aptitude et al. 
 
Could this be your problem?

---

### Post by richieza on 2011-11-17
> **ballantony said:**
> I have this exact same problem at home and work.  The big problem I have is authenticating against a windows proxy at work.  I can see the internet via firefox at work if I change the proxy settings, I need to use NTLMAPS to authenticate through the proxy to use aptitude et al. 
 
Could this be your problem?
@ballantony unfortunately this is not my problem, but thx for advise.

At varsity where proxy need everything(proxy is unix/linux based)
problem im having is I cant seem to turn proxy off to use internet at home.

---

