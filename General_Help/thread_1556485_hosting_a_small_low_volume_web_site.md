---
title: "hosting a small low volume web site"
date: 2010-08-19
forum: General Help
---

### Post by millermayhem on 2010-08-19
After searching I cannot find what I am looking for.  My wife has comissioned me to put together a cheap website to highlight her crochet projects. I had used OSX's web site server in the past. I have no idea where the folder for web sites are in Ubuntu.  This would get very low traffic and would be fine on a desktop computer.  I see no reason to install Ubuntu server.

Thank you for any advice

---

### Post by timZZ on 2010-08-19
/var/www

You need to look into apache web server and make sure you either have a dedicated IP, Dyn-DNS or a lot of patience to keep changing the IP for your Domain name.

---

### Post by mike555 on 2010-08-19
regular web hosting is only $50. a year for a small site or even free through blog sites , you might want to do that instead.

---

### Post by Zill on 2010-08-19
millermayhem:  You might like to take a look at [Opera Unite]("http://unite.opera.com/guide/") which "...allows you to share, connect and collaborate directly between computers across the Web, without going through a central, third-party server."

Caveat:  I have not used Opera Unite and so cannot comment on how well it works or how secure it is.  Personally, I would regard *any* server running on my PC as a security risk, particularly one running in a closed-source browser.  Others may give further advice on these risks.

---

### Post by silbak04 on 2010-08-19
Yeah the best thing to do is to go ahead and get free domain name...you can either google free domain or just go to [http://www.dyndns.com/](http://www.dyndns.com/) and obtain a free one. Also for the web hosting...just learn apache, it's very simple and convenient.

---

### Post by lisati on 2010-08-19
Hi all. I've been running a low volume web site and email server since January. 

If all you want is something to dish out web pages, a simple installation of Apache should help get you started. 

A static IP isn't essential if all you're doing is hosting web pages - both [no-ip]("http://no-ip.com") and [dyndns]("http://dyndns.com") have a server-side program that you can set up as a cron job to help make sure that the IP address associated with your domain name is kept up-to-date. Some routers even have an option to do the update for you, which could save you some of the hassle.

There are options for creating your web pages: [Kompozer]("http://kompozer.net/") (which is available in the repositories) might be worth checking out.

Several of us here at the forums have had some experience building our own websites and blogs etc, so feel free to ask questions.

---

