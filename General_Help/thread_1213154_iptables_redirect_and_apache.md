---
title: "iptables redirect and apache"
date: 2009-07-14
forum: General Help
---

### Post by bfuzze on 2009-07-14
I'm not sure if this is an iptables issue or and apache config issue.

I need to access a virtualhost site on my dev box from another machine.  I tried setting up some iptables rules to forward requests for a specific port (82) to the local-ip (127.0.1.1) on the dev box.  I can see from the apache error logs that it is receiving the request, but for some reason it is looking for the htdocs folder which is the default root folder, but not the doc_root of the virtual host, so either the iptables policy is not correct or it doesn't recognize the virtualhost config.

These are the iptable rules I added:
```

sudo iptables -t nat -A PREROUTING -p tcp -i eth0 -d 10.10.2.53 --dport 82 -j DNAT --to 127.0.1.1

sudo iptables -A FORWARD -p tcp -i eth0 -d 127.0.1.1 --dport 82 -j ACCEPT

```

---

### Post by bfuzze on 2009-07-14
I figured out another way to do this.  I always used /etc/hosts to designate local ips to separate domains.  I didn't realize /etc/hosts could be used to mimic a dns server, or map outgoing requests to another machine where both machines are on an internal network...

On the source machine I modified the /etc/hosts:
[dest-ip] [dest-domain(s)]

In my case, I have multiple domains across multiple ports so on the destination machine I setup the separate vhost-configs like so:

Listen 81
NameVirtualHost *:81
<VirtualHost *:81>
   ServerName domain1
   DocumentRoot ...
   ...
</VirtualHost>

Listen 82
NameVirtualHost *:82
<VirtualHost *:82>
   ServerName domain2
   DocumentRoot ...
   ...
</VirtualHost>

When using multiple ports, I had to specify the port number in the url.  The domain name by itself would not work, but I think this can be resolved by doing a redirect based on requested domain name.

---

