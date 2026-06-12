---
title: "ssh port 80"
date: 2009-09-01
forum: General Help
---

### Post by gishaust on 2009-09-01
hi

I am running  my web server on port 80. I am wondering can I ssh through the same port if I port forward and how would I do that?

thanks

---

### Post by lykwydchykyn on 2009-09-01
I don't believe it's possible to have two services listening on the same port, but if I'm wrong someone correct me.

Why would you want to do this?

---

### Post by denver on 2009-09-01
You can port forward, BUT if you do so, Apache will no longer work. All connections destined for port 80 will be forwarded to port 22 (sshd). You will be able to ssh in using port 80, but you would not be able to view any web pages.

Why on earth would you want to ssh in through port 80 anyway?:)

---

### Post by denver on 2009-09-01
You can port forward, BUT if you do so, Apache will no longer work. All connections destined for port 80 will be forwarded to port 22 (sshd). You will be able to ssh in using port 80, but you would not be able to view any web pages.

Why on earth would you want to ssh in through port 80 anyway?:)

---

### Post by falconindy on 2009-09-01
I wouldn't recommend letting two services listen on the same port. I've never tried it, but I'm somewhat doubtful that it would be easy to setup. If you're able to port forward, why not just use the standard port 22 for SSH?

Edit: With enough time and money, anything is possible. There's evidence on the interwebs that you could write a script to listen on port 80 instead of the two services, and inspect the headers in the traffic that comes through, redirecting appropriately. But, really... why?

---

### Post by gishaust on 2009-09-01
I am trying to get thought the school proxy

---

### Post by denver on 2009-09-01
If its a HTTP proxy, and the only outbound traffic allowed is through that, you can forget it :). Proxyes usualy examine the packet type/content and the requests inside. If its not a valid HTTP request/response, its discarded.

Talk to your admin for permission to use other network resources.

Sorry for the double post earlier.

---

### Post by gishaust on 2009-09-01
we use the proxy server to download software eg netbeans and do updates to do this we had to proxy.blab.ed in the browser proxies settings before that we could only surf the web.  is this of any assistance?

---

### Post by falconindy on 2009-09-01
As a former network admin, I try not to encourage people to circumvent proxies and other measures taken to **protect** networks... that said, you might consider connecting to SSH on port 443 instead of 80, since this is also a valid http port (secure http). However, as *denver* mentions, if this is a solid http proxy, it's likely looking for properly formed headers and your non-http traffic will be discarded.

---

### Post by gishaust on 2009-09-01
thanks for your help

---

