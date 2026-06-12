---
title: "Check to see if port is open and who is using it"
date: 2010-01-04
forum: General Help
---

### Post by Silvernail on 2010-01-04
I need to check to see if a port is open and who is using it.
What application does that?

[http://www.grc.com](http://www.grc.com) tells me that port 1935 is used by micromedia and port 6667 is used by irc.

As I write this post I have [http://www.ustream.tv/broadcaster/616905](http://www.ustream.tv/broadcaster/616905) open.

I would like another way to confirm this.

Thanks
Dave

---

### Post by rnerwein on 2010-01-04
hi
i don't no an application show it - but i know how to do it in a shell
1. netstat -a | more   --> look at the desired address (port) u want e.g.
 tcp        0      0 noname:41355            [www.grc.com:www](www.grc.com:www)         VERBUNDEN 
2. then use lsof to figure out which application is using that port 
lsof | grep 41355    will show you all you want i think  
firefox   13689       richi   64u     IPv4             173044      0t0 TCP    noname:41351->[www.grc.com:www](www.grc.com:www) (ESTABLISHED)
i hope this will help you
ciao

---

### Post by jonest1 on 2010-01-04
You can do the following to get a listing of established connections to see who is connecting and the pid of the local application.

```
netstat -ap | grep ESTABLISHED
```

Also, the following will give you a list of ports which are open and the pid of the application which runs on that port.

```
netstat -ap | grep LISTEN
```

I also use the netstat option of -n a lot which will give numbers for the ports instead of trying to resolve them with /etc/services.

One word of caution is that I have not tried this with Ubuntu yet, but have used it on several other Linux distros.

---

### Post by Silvernail on 2010-01-06
Thanks I can find what I need to know.

I need this for something that  has come up since I posted. 
The original question was that I could not view my upstream to 'ustream.tv'.
Turned out I had the wrong URL.

Marked solved
Thanks again

---

