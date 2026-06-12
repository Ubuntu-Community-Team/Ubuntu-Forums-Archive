---
title: "Help with running Apache and website?"
date: 2011-02-11
forum: General Help
---

### Post by GrantStoner on 2011-02-11
So, I've looked all over the Internet for how to host my own website - viewable to others - from my laptop using apache. Every web page gave me different chunks of info for various config files and directories and whatnot. But I can't figure out what to do with the info. And nowhere tells me how to make my site viewable for others, instead of just using "localhost" in the address bar. Help anyone? I'm looking for how to host my own website from my laptop. So far all I've done is a lot of reading, and ```
sudo apt-get install -y apache2
``` And I have apt-get configured to install all suggested and recommended packages.

---

### Post by sydbat on 2011-02-11
Well...as far as I know, you have to have a static IP address that you point your domain name to...then you set up your webspace associated to that IP address.

Running a website from your "laptop" will require you to continually update your domain name pointers to whatever IP address your ISP allocates you every time you boot up. A pita, if you ask me.

---

### Post by GrantStoner on 2011-02-11
I read something about using no-ip to bind the IP to my site. But I'm not quite sure how to get my site up, in the first place. I've made plenty of websites before, but never hosted my own from my own server. I let the other free web-hosts deal with that for me. ^_^

---

### Post by lisati on 2011-02-11
When I started running my own website, getting a static IP address only mattered when I was looking into setting up the email side of things. Both [DynDNS]("http://www.dyndns.com/") and [No-IP]("http://www.dyndns.com/") have server-side clients that can take care of updating the relevant records when a dynamic IP address changes, and some routers have similar capabilities built in too.

Edit, extremely short setup guide: What I initially did was to install LAMP, create some web pages, place them in the folder /var/www, and use no-ip to manage the DNS related stuff. Things have grown since then.

---

### Post by Joe of loath on 2011-02-11
Build your website, chuck it in /var/www, set up port forwarding with your router, and set up no-ip or dyndns with your router/laptop.

---

### Post by GrantStoner on 2011-02-11
Thanks. I'll try to do a little more Googling and figure out how to do each of those. In the meantime, can you point me to a forum or tutorial/guide you learned from? I'm looking for something complete that can really describe to me every step I need to take (and explain what's going on maybe). Sorry, I'm such a newbie with this stuff. ^_^

---

