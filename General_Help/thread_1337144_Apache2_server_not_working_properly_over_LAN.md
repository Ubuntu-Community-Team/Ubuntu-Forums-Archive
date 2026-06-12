---
title: "Apache2 server not working properly over LAN"
date: 2009-11-25
forum: General Help
---

### Post by bobonthenet on 2009-11-25
I'm using Ubuntu 9.04 and apache2 to host 4 different websites on the same PC each with their own unique domain name.  This works just fine when trying to view the website from outside of the LAN but typing in the URL of a website from another PC on the LAN results in a "The Connection was Reset".  Thru trial and error I have discovered that I can view websites within the lan by going to [http://server.ip/sitedirectory](http://server.ip/sitedirectory) which is fine for the most part except that wordpress doesn't like that very much.  How can I set up my hosting so that I am able to access the websites on my site the same way thru both the LAN and remotely?

---

### Post by bobonthenet on 2009-11-25
Bump.  I've tried messing with the hosts file but I've not been able to accomplish anything.  My own efforts have turned up nothing.

---

### Post by fragos on 2009-11-25
You could try using the IP of your host as in [http://192.168.0.1](http://192.168.0.1)

---

### Post by bobonthenet on 2009-11-25
> **fragos said:**
> You could try using the IP of your host as in [http://192.168.0.1](http://192.168.0.1)

You mean like I said I was doing in my first post?  That doesn't work with wordpress because of the way it is set up.  If it was just me I would use something other than wordpress but this is for my wife.  I don't think this is the place to go into wordpress configuration.  I would really like to be able to fix this on the server side instead of messing with PHP.

---

### Post by dcstar on 2009-11-25
> **bobonthenet said:**
> I'm using Ubuntu 9.04 and apache2 to host 4 different websites on the same PC each with their own unique domain name.  This works just fine when trying to view the website from outside of the LAN but typing in the URL of a website from another PC on the LAN results in a "The Connection was Reset".  Thru trial and error I have discovered that I can view websites within the lan by going to [http://server.ip/sitedirectory](http://server.ip/sitedirectory) which is fine for the most part except that wordpress doesn't like that very much.  How can I set up my hosting so that I am able to access the websites on my site the same way thru both the LAN and remotely?

By the sound of it you are using NAT, and your network is trying to connect to your External IP address from the inside, which is not possible.

You need to add entries in your internal DNS server (or hosts files) pointing the external domain name to the internal web server IP address.

---

### Post by bobonthenet on 2009-11-25
dcstar, perhaps I'm not understanding correctly.  I added an entry to my /etc/hosts file that looked like this.  Then restarted apache.

```
mydomain.com  host.ip.address
```

Then when trying to access the website locally by using mydomain.com the browser times out.  The example is how I understood your instructions.  Did you mean for me to try something else?

Can you give me an example of how this should look.

---

### Post by dcstar on 2009-11-26
> **bobonthenet said:**
> dcstar, perhaps I'm not understanding correctly.  I added an entry to my /etc/hosts file that looked like this.  Then restarted apache.

```
mydomain.com  host.ip.address
```

Then when trying to access the website locally by using mydomain.com the browser times out.  The example is how I understood your instructions.  Did you mean for me to try something else?

Can you give me an example of how this should look.

Nothing to do with Apache, you have to fix the **LAN clients** DNS lookups.

---

### Post by fragos on 2009-11-26
My etc/hosts:

127.0.0.1	localhost
127.0.1.1	Geo

"Geo" is in etc/hostname.

In leu of an IP I can address this box as "Geo.local".

Perhaps this will be helpfull.

---

