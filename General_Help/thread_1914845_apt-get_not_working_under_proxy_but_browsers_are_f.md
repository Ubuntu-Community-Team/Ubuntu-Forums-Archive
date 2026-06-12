---
title: "apt-get not working under proxy but browsers are fine"
date: 2012-01-25
forum: General Help
---

### Post by arunharidas on 2012-01-25
```
Failed to fetch http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/oneiric/main/source/Sources  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
```

this is what i get when i download using synaptic on my  11.10 ubuntu. I am using the network of my college. I know they are using squid with microsoft forefront.

i tried this but it couldnt help. 
[http://ubuntuforums.org/showthread.php?t=1589510](http://ubuntuforums.org/showthread.php?t=1589510)

browsers are fine. but neither apt-get or wget is working.

---

### Post by jerrrys on 2012-01-25
Im not behind a proxy, but know of this:

[https://help.ubuntu.com/community/AptGet/Howto#Temporary_proxy_session](https://help.ubuntu.com/community/AptGet/Howto#Temporary_proxy_session)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+proxy&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+proxy&sa=Search&cof=FORID:9)

good luck

---

### Post by arunharidas on 2012-01-26
no .. it didnt work

---

### Post by zman58 on 2012-08-14
At work all of our systems are behind a windows proxy server. The proxy server requires user account and password in encrypted form. I have had many problems trying to get apt-get to work through the proxy until I discovered cntlm.
cntlm is a proxy daemon that you run locally on your system. It provides a local proxy for the system to use and it also works with a network proxy by providing the required credentials. You can set the credentials by specifying a hash instead of user:password in the config file.
If you are having problems with proxy authentication in a corporate environment, cntlm is what you need to resolve it. Once you set it up, you can just use your Linux system.
I just downloaded the .deb file and installed it. I then followed the instructions for setting it up with hashes. It works great.

It may be also in the apt repositories, but instead I just downloaded the latest stable version .deb file through sourceforge and used that.

[http://cntlm.sourceforge.net/](http://cntlm.sourceforge.net/)

---

