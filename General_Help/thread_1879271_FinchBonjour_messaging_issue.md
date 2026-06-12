---
title: "Finch/Bonjour messaging issue"
date: 2011-11-11
forum: General Help
---

### Post by NertSkull on 2011-11-11
So, I'm trying to set up Finch using Bonjour between to computers on my LAN to talk.

I've got Finch up and running on both my upstairs and downstairs computer.  I can see each user on the other computer.  

But when I try to send a message, I get an error message "Unable to send the message, the conversation couldn't be started"

So I tried finch in debugging mode and I get this

```
&#9474;08:22:19 dns: Successfully sent DNS request to child 2307   &#9474;        &#9618;&#9474;
&#9474;08:22:19 dns: Got response for                              &#9474;        &#9618;&#9474;
&#9474;'fe80::22cf:30ff:fe78:fc23%2'                               &#9474;        &#9618;&#9474;
&#9474;08:22:19 dnsquery: Error resolving                          &#9474;        &#9618;&#9474;
&#9474;fe80::22cf:30ff:fe78:fc23%2:                                &#9474;        &#9618;&#9474;
&#9474;Address family for hostname not supported                   &#9474;        &#9618;&#9474;
&#9474;08:22:19 proxy: Connection attempt failed: Error resolving  &#9474;        &#9618;&#9474;
&#9474;fe80::22cf:30ff:fe78:fc23%2:                                &#9474;        &#9618;&#9474;
&#9474;Address family for hostname not supported                   &#9474;        &#9618;&#9474;
&#9474;08:22:19 bonjour: Error connecting to buddy Upstairs@fortex &#9474;        &#9618;&#9474;
&#9474;at fe80::22cf:30ff:fe78:fc23%2:53297 error: Error resolving&#9618;&#9474;        &#9618;&#9474;
&#9474;fe80::22cf:30ff:fe78:fc23%2:                               &#9618;&#9474;        &#9618;&#9474;
&#9474;Address family for hostname not supported 
```

It appears to me that there is some issue with IPv6 and finch???

I feel like I'm so close, but not quite there to message between these to computers command line.

I'm really hoping someone else has run into this obscure problem before and can point me in the right direction.

---

### Post by NertSkull on 2011-11-11
So it appears that it is some issue with IPv6.  I don't know what it is.

But, I did the following and it works now.

```
sudo nano //etc/avahi/avahi-daemon
```

Then, I changed this

```
use-ipv4=yes
use-ipv6=yes

```

To looke like this

```
use-ipv4=yes
use-ipv6=no

```

Now my messages come through.

But I have one other problem now that I hope someone can help with.

I want to let the upstairs computer connect with Pidgin (using bonjour) now (while I connect through SSH to the downstairs computer using Finch).

But firewall is making the difficult.  With my firewalls off, all goes great.  If I enable the firewall on the downstairs computer (running finch) everything is great.

BUT, if I enable the firewall on the upstairs computer (using pidgin) I get blocked.  

I found which port pidgin is using through netstat. BUT, each time pidgin starts, that port changes.  So each time I start pidgin I would have to change the port in my firewall.

That's clearly not very convenient.

Does anyone know why pidgin changes my port?  Or how to force it to use the same one always?  Or any way to fix this.

I'm so close to getting this working properly.

---

### Post by NertSkull on 2011-11-12
Sorry to bump, but I'm hoping someone has dealt with this pidgin port issue before.

---

### Post by NertSkull on 2011-11-15
bump, sorry

---

### Post by NertSkull on 2011-11-21
And again

---

### Post by NertSkull on 2011-12-07
bump

---

