---
title: "How to host website on my own machine"
date: 2010-09-22
forum: General Help
---

### Post by unckybob on 2010-09-22
I've heard that all one needs to do to host a website is to install apache2 and then create my own webpages in /var/www. Like I could start out putting a file "index.html" in /var/www and it would show up on the web. 

If this is true, what would my website address be on the web?

---

### Post by timgood on 2010-09-22
> **unckybob said:**
> I've heard that all one needs to do to host a website is to install apache2 and then create my own webpages in /var/www. Like I could start out putting a file "index.html" in /var/www and it would show up on the web. 

If this is true, what would my website address be on the web?

Not quite as simple as that, I'm afraid. It is possible for you to host your own domain, and it is much easier to do that if you have a static ip address from your ISP. You would need to have a registered domain and have it entered in DNS servers. You can allow access to your machine without a domain name (using an ip address rather than a .com etc address. There are also services available that will update your ip address if it is dynamic rather than static, thus allowing access to your pages constantly. Google is your friend on this. 

Hope this helps.

---

### Post by robsoles on 2010-09-22
Not entirely true.

Without exposure at your modem the website wouldn't be accessible from the internet. You could set up Apache2, pop whatever you like in the filespace it is using for web-service and then access it using [http://localhost/](http://localhost/) from the machine it is actually on.

Look up port forwarding to enable public access to your new website.

If you have a fixed IP address you could get a domain name pointed at it quite easily - if you have dynamic IP address it is far from impossible to have a domain name 'follow it' but you would need somebody like [www.dyndns.com](www.dyndns.com) to help you with that.

If you only want to host one site then the vanilla install of Apache2 may do you but you may want to read up more and checkout php-mysql and other bits and pieces relating to the task.

---

### Post by unckybob on 2010-09-22
The "http://localhost/: worked. Thanks for that. 

I'm only hosting one website. Just working with the IP address is okay. 

Can you tell me how to do the port forwarding just to get me on the net?

---

### Post by robsoles on 2010-09-22
You are looking to forward port 80 from the internet to the machine hosting the website.

You need to search Google or your preference of search engine to find instructions for your modem.

---

### Post by unckybob on 2010-09-24
Once I take care of the port forwarding. What will my address be on the WWW?

---

### Post by robsoles on 2010-09-24
To find out your (current) public IP address you can use a web service.

I keep forgetting everyone else's so I made my own: [www.robsfreespace.com/yourip/](www.robsfreespace.com/yourip/)

EDIT: You need to visit it from a machine on the same network (using same modem/router) as the machine you are using to host your site - you can visit it from the same machine you are hosting with if you have a web-browser installed on it.

---

