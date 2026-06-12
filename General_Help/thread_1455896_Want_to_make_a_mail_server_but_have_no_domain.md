---
title: "Want to make a mail server but have no domain"
date: 2010-04-16
forum: General Help
---

### Post by DanB91 on 2010-04-16
I recently decided I wanted a web server so I installed Ubuntu and apache2 on it and it works fine.  I installed forums on the site as well and it's working fine to.  Problem I don't know exactly what to do with the site so I haven't purchased a domain yet (so to access the site you just type in the ip address). 

I know this sounds really weird but I want to know if I can make a mail server without a domain name.  I kinda want to use it for e-mail verification for the forum.  I have been following this tutorial: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)  and it seems i need a domain name.  Is it possible?

Also I am not using Ubuntu server, would setting up a mail server be much easier on there (or rather, does it come with a mail server?)  Thank you very much

---

### Post by jpaugh64 on 2010-04-16
Well, first of all, you might be able to use the hostname instead of the ip address, if you are accessing it from a LAN, where all computers have either avahi (for linux) or bonjour (Mac) installed. (I'm not sure about Windows; Active Directory stuff, I think). As for the domain, you might try using the .local domain. Also, I read somewhere that you can send email to person@X.X.X.X--an ip address.

---

### Post by KdotJ on 2010-04-16
There are places that allow you to create free domains. For example I you have a dynamic IP address, You can go to dyndns.org and can select a free sub domain. You can then point your new free domain to your IP address. You may have to set up port forwarding on your router to allow people to be directed to the server.

---

### Post by DanB91 on 2010-04-16
Thanks for help both of you.  I will prob use dyndns.  My second question is user version of Ubuntu best for a webserver/mail server?  The tutorial is kinda a pain in the ***.  Does the server version come with a mail server?

---

### Post by lisati on 2010-04-16
I have free domains at both dyndns and [noip]("http://noip.com")

Both of these services have tools you can download to help keep the relevant DNS lookup information updated automatically - useful if you have a dynamically assigned public IP address. Your router might also have an option to do this for you without you having to install extra stuff.

Edit: I use apache2 for the web server part of my system, and postfix for the email. I also have squirrelmail installed, which acts a bit like webmail.

---

### Post by DanB91 on 2010-04-17
> **lisati said:**
> I have free domains at both dyndns and [noip]("http://noip.com")

Both of these services have tools you can download to help keep the relevant DNS lookup information updated automatically - useful if you have a dynamically assigned public IP address. Your router might also have an option to do this for you without you having to install extra stuff.

Edit: I use apache2 for the web server part of my system, and postfix for the email. I also have squirrelmail installed, which acts a bit like webmail.

Thanks, I did use a no-ip domain.  I am following the tutorial that i have said i am following in the OP.   I cannot figure out how to get this working for life of me.  Is there an easier way than this?  I am sending mail to [email]root@mail.myno[/email]-ipdomain  and i get fail to send messages.  

Thanks for the help

---

