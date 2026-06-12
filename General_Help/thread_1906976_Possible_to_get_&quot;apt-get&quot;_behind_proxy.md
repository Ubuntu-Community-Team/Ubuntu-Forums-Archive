---
title: "Possible to get &quot;apt-get&quot; behind proxy??"
date: 2012-01-10
forum: General Help
---

### Post by airplanesimen on 2012-01-10
HI! I am confused, because i am trying to get my terminal to use "apt-get", but it wont download or install anything, (like apt-get update) because my school network is using a proxy which is:
 Proxy.troms.vgs.no:80
i have enabled the proxy in the network settings, but it doesnt seem to work for the terminal, because i need a username and a password, and i cant set my username or password anywhere :(.  

i dont know, but i think it is the same problem when i am using the internet browser (on https sites):
i can use my network-browser normally, except when i am trying to access https:// sites on the web, then it totally locks (the browser). --> Firefox is saying it is some kind of certificate error, and i cant browse on those sites :S (i cant even make an exception..). When i start the browser, i manually enter the pass and username.

Any suggestion is welcome! Thanks a lot :P

---

### Post by Lars Noodén on 2012-01-10
You can make the proxy setting permanent by editing [font=Courier New]/etc/apt/apt.conf[/font]

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

---

### Post by airplanesimen on 2012-01-10
> **Lars Noodén said:**
> You can make the proxy setting permanent by editing [font=Courier New]/etc/apt/apt.conf[/font]

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

And what should i write? Thanks for a quick reply! ;) when i enter the file, the file is empty :S

---

### Post by Lars Noodén on 2012-01-10
If the information you supplied above is accurate then it should be something like this:

```

Acquire::http::Proxy "http://proxy.troms.vgs.no:80";

```

But the port number looks suspect.  That is not the usual port number for proxies.

---

### Post by airplanesimen on 2012-01-11
> **Lars Noodén said:**
> If the information you supplied above is accurate then it should be something like this:

```

Acquire::http::Proxy "http://proxy.troms.vgs.no:80";

```

But the port number looks suspect.  That is not the usual port number for proxies.

I am aware of that, but really, it is port 80, i use it for the whole system right now, and it works fine :P 

But is it possible to use username and password (and domain)in the same line? maybe: 
```

Acquire::http::Proxy "http://Domain\\Username:password@proxy.troms.vgs.no:80";

```
??? Thanks again

---

### Post by airplanesimen on 2012-01-11
W: Could not get [http://archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-i386/Packages)  407  Proxy Authentication Required [IP: 193.161.89.201 80]

Any possible way to get authentication in apt.conf file?

Edit:: 

I found the solution: I Had to write this if i had proxy authentication: (in the /etc/apt/apt.conf file)
```

Acquire::http::Proxy "http://username:password@proxyserver:port/";

``` and for me i had to write:
```

Acquire::http::Proxy "http://simla190995:PASSWORD@Proxy.troms.vgs.no:80/";

```

---

