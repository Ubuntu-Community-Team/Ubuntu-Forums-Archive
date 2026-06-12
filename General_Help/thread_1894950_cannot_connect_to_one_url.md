---
title: "cannot connect to one url"
date: 2011-12-13
forum: General Help
---

### Post by virtdave@mcn.org on 2011-12-13
Since (maybe) a recent update (of ubuntu 11.10) I cannot connect to the URL [www.xe.com](www.xe.com).  I can do so using a computer with Windows Vista.  In Ubuntu, I then tried pinging [www.xe.com](www.xe.com), and it times out without response (I tried pinging [www.google.com](www.google.com) first, and it pings--and loads--just fine).  Any ideas?

---

### Post by duke.tim on 2011-12-13
What is the error message from the web browser?

---

### Post by virtdave@mcn.org on 2011-12-13
There's no error message, Firefox (and likewise Chromium) just indicates "connecting...." forever, but nothing happens...and as I mentioned, when I type (in the Terminal) ping [www.xe.com](www.xe.com), there's no result.

---

### Post by Habitual on 2011-12-13
> **virtdave@mcn.org said:**
> There's no error message, Firefox (and likewise Chromium) just indicates "connecting...." forever, but nothing happens...and as I mentioned, when I type (in the Terminal) ping [www.xe.com]("http://www.xe.com"), there's no result.

try 
```
ping xe.com
```instead.

and try this in your browser:
[http://216.220.38.24](http://216.220.38.24)

If that works, I suspect your DNS Nameservers may need to be updated...

you could also try google's dns resolvers...
```
cp /etc/resolv.conf /etc/resolv.conf.orig 
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" > resolv.conf
```

---

### Post by virtdave@mcn.org on 2011-12-13
nope....xe.com gets the same (non)response as [www.xe.com]("http://www.xe.com") both in browser and in attempt to ping, as does using the IP addresses.  and when I try the cp /etc.... in the terminal, I'm told 'permission denied'--and the other google resolver thingy doesn't help either....the terminal does accept the echo -e..... stuff, but nothing results.

---

### Post by virtdave@mcn.org on 2011-12-13
well golly.  It turns out the problem was in my router!  I was misled because I could ping xe.com from a computer with an ethernet connection which did not go through the router, but not (when I later checked it) thru a third computer which shared the router with the computer with ubuntu on it.  I rebooted the router, now I can connect to xe.com.  It's a great mystery why my router seemed to be able to let me connect to every other website I tried, just not to xe.com.  Another Mystery of the Internet.  Thanks for your efforts

---

### Post by Habitual on 2011-12-14
+1 fixing it yourself. :KS

---

