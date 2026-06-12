---
title: "Web Hosting for newbie"
date: 2010-05-03
forum: General Help
---

### Post by coloradocroat on 2010-05-03
I have a question or several on web hosting on Ubuntu.  I have a Ubuntu Machine setup by an old employee that is running our current website.  Unfortunately I don't know where the files are on the machine or how he directs them.  That website was built by Frontpage.  

What I would like to do is start from scratch, and have a box that hosts multiple websites.

Here are my questions:

1. What version of Ubuntu should I install?  This will be an old Windows XP Pro Box
2. Will I be able to create a website in WebExpressions 2 and upload to an Ubuntu Box?
3. Where do I put the website files and how do I direct an outside request (Port 80) to those files when someone types in the website. (I know all the pieces up to the box itself.  The question is about the direction to the files by Ubuntu) 
4. Can one box host multiple different websites and how do I direct them correctly so that when someone enters xyz.com they don't get the website for abc.com that is on the same box.

I hope that is clear enough.  Thank you,

---

### Post by Mazin on 2010-05-03
1. Ideally, you would use Ubuntu Server Edition, but because its meant for dedicated servers, it doesn't come with a graphical interface.  Otherwise, Ubuntu Desktop would work.

2. Yes... but any proprietary Microsoft extensions probably will not work out of the box (ASP, FrontPage server extensions, etc.)

3. If the Apache2 server is up and running, it will automatically handle web requests on port 80.

4. You need to set up your stuff in /etc/apache2/sites-enabled
Try this guide: [http://wiki.gandi.net/en/hosting/using-linux/tutorials/ubuntu/virtualhosts](http://wiki.gandi.net/en/hosting/using-linux/tutorials/ubuntu/virtualhosts)


**The real answer is:** if you and your employer value your time and money, you will buy a shared hosting plan from the likes of [1&1]("http://www.1and1.com/?affiliate_id=187654") or [Dreamhost]("http://www.dreamhost.com/r.cgi?672447").  You will waste a lot of time and money trying to manage your own server when you could just pay less than $10/month for a shared hosting account.

---

