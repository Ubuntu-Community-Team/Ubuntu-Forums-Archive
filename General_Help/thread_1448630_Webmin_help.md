---
title: "Webmin help"
date: 2010-04-06
forum: General Help
---

### Post by borischan on 2010-04-06
Hi all, hope I can ask a question to any webmin users out there.
I built a Ubuntu server, 8.04, and I am running webmin. For the most part all is well, but I'm stuck with web hosting.

Currently I have a website hosted, domain name from DoDaddy, and a fixed IP address. GoDaddy set up is OK, if I type in my URL from anywhere, it successfully directs to my machine. OK so far...

My site is stored in var/www/mysite

If I type in my IP address, this also points to my site. 
Now, I want to at some stage host other sites. How do I configure for example IP address to point at a holding page, [http://mysite](http://mysite) to direct to mysite, [http://newsite](http://newsite) to direct to new site etc.

Sorry for the newbie question, this is giving me a headache:)

Any help would be appreciated

---

### Post by v1ad on 2010-04-06
hmm i'm not sure how you would do it through webmin, you will have more luck through ssh. but by hosting other sites you will need another ip address from my experience, but i could be wrong. your server redirects it to the folder. the your url just redirects it to the ip.

---

### Post by borischan on 2010-04-07
> **v1ad said:**
> hmm i'm not sure how you would do it through webmin, you will have more luck through ssh. but by hosting other sites you will need another ip address from my experience, but i could be wrong. your server redirects it to the folder. the your url just redirects it to the ip.

I know it's possible, webmin offers vitual servers, should be able to host many sites with one IP. I found a useful thread [http://ubuntuforums.org/showthread.php?t=1368918](http://ubuntuforums.org/showthread.php?t=1368918)
Checking it out now.

Webmin documentation usually assumes you know what you are doing:)

---

