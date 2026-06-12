---
title: "polipo tor vuze and firefox"
date: 2010-02-17
forum: General Help
---

### Post by Forbees on 2010-02-17
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

did everything in here, and i don't have tor working w/ firefox

this is what happened after editing the config file
```

xcr@xcr:~$ sudo gedit /etc/polipo/config
xcr@xcr:~$ sudo /etc/init.d/tor restart
Stopping tor daemon: tor.
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Feb 17 22:33:25.657 [notice] Tor v0.2.1.23. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Feb 17 22:33:25.659 [notice] Initialized libevent version 1.4.11-stable using method epoll. Good.
Feb 17 22:33:25.659 [notice] Opening Socks listener on 127.0.0.1:9050
done.
xcr@xcr:~$ sudo /etc/init.d/polipo restart
Restarting polipo: /etc/polipo/config:10: parse error.
/etc/polipo/config:25: parse error.
/etc/polipo/config:37: parse error.
/etc/polipo/config:61: parse error.
/etc/polipo/config:70: parse error.
polipo.

```

for some reason polipo is erroring . . . and i get 0 hits when googling the errors

when testing tor w/ the firefox plugin it tells me to check my polipo settings after an error

i used apt-get to install polipo

---

### Post by nixclusive on 2010-02-17
cat you paste the contents of your polipo config file? it can be located at /etc/polipo/config

You can use the following command to filter out comments:
```
egrep -v "^#|^$" /etc/polipo/config
```

---

### Post by Forbees on 2010-02-18
```

xcr@xcr:~$ egrep -v "^#|^$" /etc/polipo/config
proxyAddress = &#8220;127.0.0.1?
proxyPort = 8118
allowedClients = 127.0.0.1
allowedPorts = 1-65535
proxyName = &#8220;localhost&#8221;
cacheIsShared = false
socksParentProxy = &#8220;localhost:9050?
socksProxyType = socks5
chunkHighMark = 33554432
diskCacheRoot = &#8220;&#8221;
localDocumentRoot = &#8220;&#8221;
disableLocalInterface = true
disableConfiguration = true
dnsUseGethostbyname = yes
disableVia = true
censoredHeaders = from,accept-language,x-pad,link
censorReferer = maybe
maxConnectionAge = 5m
maxConnectionRequests = 120
serverMaxSlots = 8
serverSlots = 2
tunnelAllowedPorts = 1-65535

```

---

### Post by nixclusive on 2010-02-18
You'll probably want to re-quote the values in quotes again.

```
&#8220; is not the same thing as "
```

So the corrected values would look like:
```
proxyAddress = "127.0.0.1"
proxyName = "localhost"
socksParentProxy = "localhost:9050"
diskCacheRoot = ""
localDocumentRoot = ""
```

---

### Post by Forbees on 2010-02-19
```

xcr@xcr:~$ sudo /etc/init.d/polipo restart
Restarting polipo: polipo.
xcr@xcr:~$ sudo gedit /etc/polipo/config
xcr@xcr:~$ egrep -v "^#|^$" /etc/polipo/config
proxyAddress = "127.0.0.1"
proxyPort = 8118
allowedClients = 127.0.0.1
allowedPorts = 1-65535
proxyName = "localhost"
cacheIsShared = false
socksParentProxy = "localhost:9050"
socksProxyType = socks5
chunkHighMark = 33554432
diskCacheRoot = ""
localDocumentRoot = ""
disableLocalInterface = true
disableConfiguration = true
dnsUseGethostbyname = yes
disableVia = true
censoredHeaders = from,accept-language,x-pad,link
censorReferer = maybe
maxConnectionAge = 5m
maxConnectionRequests = 120
serverMaxSlots = 8
serverSlots = 2
tunnelAllowedPorts = 1-65535

```

i no longer get errors when starting polipo

but i still have tor not working apparently, firefox's plugin gives me the same error, and the tor test page returns negative

---

### Post by Forbees on 2010-02-19
anyone?

---

### Post by nixclusive on 2010-02-20
I'm assuming you are using torbutton addon for firefox. Can you describe the error you are getting? Or perhaps post a screenshot.

A standard tor setup on a home pc looks like this:

```
Web Browser <---> polipo (port 8118) <---> tor (port 9050) <---> ... (internet)
```

Of the above chain, your polipo setup seems to be working fine.

---

### Post by Forbees on 2010-02-20
when i test with the tor plugin (firefox)
[IMG]http://i49.tinypic.com/160cz20.png[/IMG]

after i close the plugin preferences
[IMG]http://i48.tinypic.com/5zpd9g.png[/IMG]



and i don't think it's tor, since i get no errors from starting it
```

xcr@xcr:~$ sudo /etc/init.d/tor restart
[sudo] password for xcr: 
Stopping tor daemon: tor.
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Feb 20 19:52:51.615 [notice] Tor v0.2.1.23. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Feb 20 19:52:51.617 [notice] Initialized libevent version 1.4.11-stable using method epoll. Good.
Feb 20 19:52:51.617 [notice] Opening Socks listener on 127.0.0.1:9050
done.

```

---

### Post by nixclusive on 2010-02-21
hmmm, try enabling torbutton and goto [tor check page](http://check.torproject.org/). torbutton will probably complain about a failed last proxy check but it will enable anyway. If the testpage returns negative, disable torbutton and configure firefox to use the http(s) proxy at 127.0.0.1:8118 and socks proxy at 127.0.0.1:9050 and see the checkpage again.

btw, if you need tor connectivity ASAP I'd suggest using [Incognito LiveCD](http://www.anonymityanywhere.com/incognito/). It can also be used from within a virtual machine. (ala qemu -cdrom <image.iso>)

---

### Post by Forbees on 2010-02-21
tor button said it failed, but the test page said i'm using tor so i guess i'm okay?

how would i get vuze to work with tor? or even transmision (is that possible?)

---

### Post by nixclusive on 2010-02-21
> **Forbees said:**
> tor button said it failed, but the test page said i'm using tor so i guess i'm okay?

how would i get vuze to work with tor? or even transmision (is that possible?)
I'm not sure why torbutton is reporting a failure of even if its ok if the test page is returning positive results.

You probably want to look at [this page](http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO/BitTorrent) on help with setting up vuze, transmission, etc. to use tor network.

However, IMHO, its probably not a good idea to use bittorrent over tor as you'll get really slow speeds and you may be unwillingly congesting the already scarce tor bandwidth.

> Please *DO NOT* use Tor for routing peer-to-peer data traffic, it can not handle the bandwidth. They have indicated that they will make efforts to ban such usage if it continues, which will likely affect both legitimate and unwanted use! 

---

### Post by Forbees on 2010-02-21
and this is where i say it's not worth it

after doing some speed tests i go from 16Mb/s to 100Kb/s transfer speed . . .

noooottttt wooorrrttthhh it, theres a reason i pay for this cable . . .

---

### Post by nixclusive on 2010-02-22
lol

---

