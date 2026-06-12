---
title: "Proxychains and svn to download ffmpeg"
date: 2010-08-10
forum: General Help
---

### Post by Stoneface on 2010-08-10
As I cannot use svn to download the latest ffmpeg from trunk:
```
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
svn: Can't connect to host 'svn.ffmpeg.org': Connection refused
```

I am trying to work with proxychains. But I get errors:
```
proxychains svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
ProxyChains-3.1 (http://proxychains.sf.net)
|DNS-request| svn.ffmpeg.org 
|S-chain|-<>-127.0.0.1:9050-<--timeout
|DNS-response|: svn.ffmpeg.org is not exist
svn: Unknown hostname 'svn.ffmpeg.org'
```

Can anyone explain to me how to use proxychains properly so I can download the latest ffmpeg and compile it?

PS here proxychains.conf in /etc/proxychains.conf/:
```
# ProxyList format
#       type  host  port [user pass]
#       (values separated by 'tab' or 'blank')
#
#
#        Examples:
#
#            	socks5	192.168.67.78	1080	lamer	secret
#		http	192.168.89.3	8080	justu	hidden
#	 	socks4	192.168.1.49	1080
#	        http	192.168.39.93	8080	
#		
#
#       proxy types: http, socks4, socks5
#        ( auth types supported: "basic"-http  "user/pass"-socks )
#
[ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
socks4 	127.0.0.1 9050
```

---

### Post by Stoneface on 2010-08-10
Followed a guide @ [http://www.supermind.org/blog/702/use-proxoid-with-subversion-with-proxychains](http://www.supermind.org/blog/702/use-proxoid-with-subversion-with-proxychains) and got this result:
```
$ proxychains svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk
ProxyChains-3.1 (http://proxychains.sf.net)
|D-chain|-<>-127.0.0.1:8080-<--timeout

!!!need more proxies!!!
svn: Can't connect to host 'svn.ffmpeg.org': Connection refused
```

Better I guess, but not quite.

---

### Post by Stoneface on 2010-08-10
Tried again with another port which I opened in the wifi box

```
$ proxychains svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk
ProxyChains-3.1 (http://proxychains.sf.net)
|D-chain|-<>-127.0.0.1:64304-<--timeout

!!!need more proxies!!!
svn: Can't connect to host 'svn.ffmpeg.org': Connection refused
```

How can I add more proxies?

---

### Post by Stoneface on 2010-08-10
Added some more proxies, but only get time-outs and refusal in the end:
```
$ proxychains svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk
ProxyChains-3.1 (http://proxychains.sf.net)
|D-chain|-<>-127.0.0.1:3960-<--timeout
|D-chain|-<>-212.45.53.122:80-<--timeout
|D-chain|-<>-195.18.69.4:8080-<--timeout

!!!need more proxies!!!
svn: Can't connect to host 'svn.ffmpeg.org': Connection refused

```

---

### Post by Stoneface on 2010-08-10
New trial editing the original config:
```
$ sudo proxychains svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk
ProxyChains-3.1 (http://proxychains.sf.net)
|DNS-request| svn.ffmpeg.org 
|S-chain|-<>-212.45.53.122:80-<--timeout
|DNS-response|: svn.ffmpeg.org is not exist
svn: Unknown hostname 'svn.ffmpeg.org'
```

---

### Post by Stoneface on 2010-08-10
Just tried to use proxychain with firefox to go to Google and got dns errors:```
$ sudo proxychains firefox www.google.nl
ProxyChains-3.1 (http://proxychains.sf.net)
App startup
|DNS-request| www.google.nl 
|S-chain|-<>-212.45.53.122:80-<--timeout
|DNS-response|: www.google.nl is not exist
|DNS-request| www.google.nl 
|DNS-request| www.google.nl 
|S-chain|-<>-212.45.53.122:80-|S-chain|-<>-212.45.53.122:80-|DNS-request| localhost 
|S-chain|-<>-212.45.53.122:80-<--timeout
|DNS-response|: www.google.nl is not exist
|DNS-request| www.google.nl 
<--timeout
|DNS-response|: www.google.nl is not exist
|S-chain|-<>-212.45.53.122:80-<--timeout
|DNS-response|: localhost is not exist
Usage:program_name [address][:port]<--timeout
|DNS-response|: www.google.nl is not exist
|DNS-request| www.stopbadware.org 
|S-chain|-<>-212.45.53.122:80-^C
me@ubuntu:/etc$ <--timeout
^C

```

Just don't get it..

---

### Post by Stoneface on 2010-08-10
I think it is a DNS resolution issue, but I do not know yet how to address this problem. Changes /etc/resolv.conf and making name server 127.0.0.1 did not really offer any help and was undone on reboot.

Source: [http://www.hermann-uwe.de/blog/anonymous-google-earth-over-tor](http://www.hermann-uwe.de/blog/anonymous-google-earth-over-tor)

---

### Post by Stoneface on 2010-08-10
Fixed Tor - tor runs well under Firefox now - and Polipo, restored /etc/proxychains.conf's old setup with ```
socks4 	127.0.0.1 9050
``` . Ran it again: ```
$ sudo proxychains svn checkout svn://svn.ffmpeg.org/ffmpeg/trunkProxyChains-3.1 (http://proxychains.sf.net)
|DNS-request| svn.ffmpeg.org 
|S-chain|-<>-127.0.0.1:9050-<><>-4.2.2.2:53-<><>-OK
|DNS-response|: svn.ffmpeg.org is not exist
svn: Unknown hostname 'svn.ffmpeg.org'
```

So I'd say better, but still a dns issue

---

### Post by FakeOutdoorsman on 2010-08-10
Another alternative is to download a nightly FFmpeg snapshot. You can download a [full checkout](http://ffmpeg.org/releases/ffmpeg-checkout-snapshot.tar.bz2) or [bare sources](http://ffmpeg.org/releases/ffmpeg-export-snapshot.tar.bz2).  The only difference is the bare sources don't contain SVN metadata.

You may also want to head over to the *#ffmpeg* IRC channel and ask if/why you are being actively blocked from *svn.ffmpeg.org*.

---

### Post by Stoneface on 2010-08-10
Did another run and yeah, all working! DNS is resolved properly and proxychains is working well together with Tor and Polipo now. I removed privoxy which I added as well, but which seemed to interfere with polipo.

@ Fakeoutdoorsman Will ask them @ IRC. Thanks again for your help!

P.S. See also [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

Update:

ffmpeg blocks certain ip ranges because certain individuals abuse the system

---

