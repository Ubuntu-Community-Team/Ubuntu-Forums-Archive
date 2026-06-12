---
title: "Interesting problem: Can't access one particular secure web page from client"
date: 2010-04-18
forum: General Help
---

### Post by dash86no on 2010-04-18
I have an interesting problem. 

I have an Ubuntu Server 8.04 set up with two NICs to act as a router/firewall/proxy/DHCP etc. 

I have a client running ubuntu 10.04

I can't connect to the following page from my client:
[https://branch.nicos.co.jp](https://branch.nicos.co.jp)

The page just won't come up. I don't have problems connecting to any other web pages. 

However, if I ssh into my server with x forwarding, and run Firefox from there, I can access the nicos.co.jp  page. 

I tried turning the firewall (shorewall) and proxy (squid) off, put I still can't access the nicos.co.jp page from the client.

If I go to proxify.com I can access the nicos.co.jp page. If I set up a proxy on the client to some random proxy i find on the Internet, then I can access the nicos.co.jp page. 

The interesting thing is, I was having this problem for the longest time but just assumed the page was unavailable on weekends. (the only time I ever check it). Then about a week ago, I realized after trying proxify.com that the problem was at my end. I then looked into my firewall rules, and realized that my redirect to squid (transparent) was commented out. Of course, this shouldn't have been a big deal (just meaning that I wasn't using the transparent proxy), but when I tried to set the redirect back it actually solved the problem and I was able to access the nicos.co.jp from my client. At the same time, I had been having problems accessing linkedin.com (which prompted me to try nicos.co.jp through proxify.com) and the same linkedin problem was also fixed at the same time. 

I did not think much of it at the time, as the problem appeared solved, but this weekend, although able to access linkedin.com (and all other sites) either going through the proxy, or else not being redirected through the proxy, I am not able to access nicos.co.jp. 

I have tried in other browsers, and even in Windows, and am just not able to access nicos.co.jp from the client. I am able to telnet to ports 443 and 80 however. 

Lynx is able to connect to the nicos.co.jp site from my server, but from the client, this fails with the following trace:

Looking up branch.nicos.co.jp first
Looking up branch.nicos.co.jp
Making HTTP connection to branch.nicos.co.jp
Sending HTTP request.
HTTP request sent; waiting for response.
HTTP/1.0 302 Moved Temporarily
Data transfer complete
HTTP/1.0 302 Moved Temporarily
Using [https://branch.nicos.co.jp/](https://branch.nicos.co.jp/)
Looking up branch.nicos.co.jp
Making HTTPS connection to branch.nicos.co.jp
Retrying connection without TLS.
Looking up branch.nicos.co.jp
Making HTTPS connection to branch.nicos.co.jp
Alert!: Unable to make secure connection to remote host.

lynx: Can't access startfile [http://branch.nicos.co.jp/](http://branch.nicos.co.jp/)


To summarize:

1: I have two computers, server and client. The client is set up with PPPoE connection on one interface, and a second interface is connected to my internal network giving DHCP services etc. 

2: I can connect to nicos.co.jp from the server, but not the client
3: I have tried stopping both the firewall, the proxy, and the firewall and proxy on the server, but the client is unable to access nicos.co.jp regardless of the configuration. 
4: The are no problems accessing other web pages (although i did have a problem with linkedin a week ago which seemed to have been fixed when I started to re-redirect traffic through my transparent squid server again). 

5: If I go through proxify.com, or else I set my client to use a publicly available proxy server, I can connect to the Nicos.co.jp page. 

Also, some extra info, I actually tried to apt-get purge squid and install squid3. The problem is the same. 

What seems weird is that this appears to not be a problem with squid or shorewall, but rather between my server and client. 


any ideas most appreciated

---

