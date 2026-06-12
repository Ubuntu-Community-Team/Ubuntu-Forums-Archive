---
title: "DNS redirect from Godaddy"
date: 2011-02-22
forum: General Help
---

### Post by anifort on 2011-02-22
Hello all, 
I recently set up ubuntu 10.10 server with ispconfig 3. Server works fine when i use my desktops host file to insert a domain and point it to the server using my isp IP address. When i change it from go daddy though, i can't make it work. 
for example my host file looks like this

81.xxx.xx.xx       [www.example.com]("http://www.example.com") 

and it works.

Now on godaddy from DNS Manager of my domain [www.example.com]("http://www.example.com")  i change the row host - points to, that looks like this:
@             97.74.215.94

to this:
@             81.xxx.xx.xx

but nothing works!

thanks,
Chris

---

### Post by Habitual on 2011-02-22
http://intodns.com/$domain.com can help you debug DNS issues.
Typically, nameservers are the culprits.

Without the actual domain name, there's not much anyone can do. </hint>

---

### Post by anifort on 2011-02-22
My bad! i was trying to insert a subdomain actually as a CNAME record instead of A record. Thanks for the help!

---

### Post by Habitual on 2011-02-22
Isn't DNS 'fun'? :KS

---

### Post by anifort on 2011-02-26
> **Habitual said:**
> Isn't DNS 'fun'? :KS

What can i say... not when it comes to write your own dns server algorithm :D put yes after all its fun

---

