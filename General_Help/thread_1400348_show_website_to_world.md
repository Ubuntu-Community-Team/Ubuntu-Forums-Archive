---
title: "show website to world"
date: 2010-02-06
forum: General Help
---

### Post by ubudog on 2010-02-06
Hello, I installed the apache web server on my laptop, running Ubuntu 9.10 desktop version.  I created a small web site using ```
sudo joe /var/www/index.html
``` and I want to make it available to the world.  Do I have to buy a domain name or something or can I just do it all from home?  I am extremely new to this.  Any help appreciated.  Thanks! ;)

---

### Post by wojox on 2010-02-06
Read this: [http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841)

---

### Post by mushwars on 2010-02-06
When I first started using apache back on windows 98 no one ever told me about port forwarding. I spent weeks fiddeling with settings eventually resorting to my router. I did some research on the things in my router like application forwarding, this lead me to what I know now about it.

Since those times, there have been strides to help average users create webpages. This can be done by going to the site

[http://portforward.com/](http://portforward.com/)

---

### Post by bpalone on 2010-02-06
If you are just wanting to play around with it to learn, there are some services that allow you to use a subdomain name such as yoursite.dyndns.com.  DynDns is one, DNSExit is another and there are others.  They also provide support for dynamic IP addresses, which most of us have.  They do most of this for free.

There are several articles on the web about hosting at home.  Most are written for windows, but the principals are the same.  Do a Google search for hosting your own site at home, you will find many.

Enjoy the journey, I did.

---

### Post by ubudog on 2010-02-06
Thank you!!!! :p:p:p:p:p

---

### Post by thecliff on 2010-02-06
Are you wanting to make your site available to everyone or just test at home?  If you want to make it available to everyone, you will have to buy a domain.

**UPDATE: --^ way wrong.  sorry**

---

### Post by mushwars on 2010-02-06
> **thecliff said:**
>  If you want to make it available to everyone, you will have to buy a domain.
wrong.

you do not even need a domain you can give people your ip address or get a free subdomain from [s][http://freedns.com/](http://freedns.com/)[/s][URL="http://freedns.com/"] http://freedns.afraid.org/
[/URL]

if you want I can give you one whatever.mushwars.net whatever being whatever you want.

I just need your IP address.
[ ]("http://freedns.com/")

---

### Post by samantha_ on 2010-02-06
> **thecliff said:**
> Are you wanting to make your site available to everyone or just test at home?  If you want to make it available to everyone, you will have to buy a domain.

you dont need to buy one. You can get a free Dynamic DNS host, such as dyndns, or if you have a static ip, you can just point people towards the ip ;)

---

### Post by mushwars on 2010-02-06
> **samantha_ said:**
> ...
we are on the same wave length ;)

---

### Post by samantha_ on 2010-02-06
> **mushwars said:**
> we are on the same wave length ;)

except that I use everydns :)

---

### Post by ubudog on 2010-02-06
> **mushwars said:**
> wrong.

you do not even need a domain you can give people your ip address or get a free subdomain from [s][http://freedns.com/](http://freedns.com/)[/s][URL="http://freedns.com/"] http://freedns.afraid.org/
[/URL]

if you want I can give you one whatever.mushwars.net whatever being whatever you want.

I just need your IP address.
[ ]("http://freedns.com/")

Thanks for the offer, but I have am going to get it set up with "whatever.homelinux.org"

---

### Post by ubudog on 2010-02-06
Is there a way to set it up so that I can keep my website at "whatever.homelinux.org" even if I'm not at my house?

---

### Post by mushwars on 2010-02-06
thats the thing about servers unfortunatly, they have to be on 24/7 and you cant just bring them to mom's house for the weekend. They have to stay put.

You will want to point your domain to your public Ip address. Then set up port forwarding on your router. And thats about it, (supposing you can access your site [http://localhost/](http://localhost/) )

---

### Post by ubudog on 2010-02-06
> **mushwars said:**
> thats the thing about servers unfortunatly, they have to be on 24/7 and you cant just bring them to mom's house for the weekend. They have to stay put.

You will want to point your domain to your public Ip address. Then set up port forwarding on your router. And thats about it, (supposing you can access your site [http://localhost/](http://localhost/) )

Thank you for your help!

---

### Post by samantha_ on 2010-02-06
[http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html)

---

### Post by ubudog on 2010-02-06
> **samantha_ said:**
> [http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html)

Thank you. :)

---

### Post by ubudog on 2010-02-07
> **mushwars said:**
> thats the thing about servers unfortunatly, they have to be on 24/7 and you cant just bring them to mom's house for the weekend. They have to stay put.

You will want to point your domain to your public Ip address. Then set up port forwarding on your router. And thats about it, (supposing you can access your site [http://localhost/](http://localhost/) )

I could fix that with remote desktop.

---

### Post by ubudog on 2010-02-07
Got it up and running!!  Thank you so much for all your help everyone!!!!  I love Ubuntu!!!!!!! :D:D:D:D

---

### Post by bpalone on 2010-02-08
Just tried you site and no joy.  Either you have it off line or it is not pointing to the proper IP. Glad you are making headway.

Enjoy!!

---

### Post by ubudog on 2010-02-09
> **bpalone said:**
> Just tried you site and no joy.  Either you have it off line or it is not pointing to the proper IP. Glad you are making headway.

Enjoy!!

When did you try?  Last night it was offline, but today I have it fixed.

---

### Post by ubudog on 2010-02-09
The server, my laptop, will be on and off.

---

### Post by mushwars on 2010-02-09
I used to run my server on my laptop. They are not designed to handle that kind of load, I never turned my laptop off though, if you want a website but cant leave the server on I recommend free hosting.

---

### Post by ubudog on 2010-02-09
> **mushwars said:**
> I used to run my server on my laptop. They are not designed to handle that kind of load, I never turned my laptop off though, if you want a website but cant leave the server on I recommend free hosting.

Free hosting?

---

### Post by lisati on 2010-02-09
> **ubudog said:**
> Free hosting?

I used to use Geocities Free, but that's no longer an option.....

Check [this]("http://lmgtfy.com?q=free+web+hosting")

---

### Post by ubudog on 2010-02-09
Thanks.

---

### Post by bpalone on 2010-02-09
Just tried again, 0318 UTC Feb. 10, 2010, and no joy,again.   As stated earlier in this thread, a server needs to be up 24/7, or as close to that as possible.

---

### Post by ubudog on 2010-02-10
> **bpalone said:**
> Just tried again, 0318 UTC Feb. 10, 2010, and no joy,again.   As stated earlier in this thread, a server needs to be up 24/7, or as close to that as possible.

Yeah, sorry.  It should be on tonight at 7:00 EST

---

### Post by bpalone on 2010-02-10
It worked this time.  Hope you continue to enjoy the learning experience.

---

### Post by ubudog on 2010-02-10
> **bpalone said:**
> It worked this time.  Hope you continue to enjoy the learning experience.

Thanks, just figured out some more html.

---

