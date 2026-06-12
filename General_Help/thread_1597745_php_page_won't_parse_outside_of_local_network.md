---
title: "php page won't parse outside of local network"
date: 2010-10-15
forum: General Help
---

### Post by lohertz on 2010-10-15
Running Apache 2.2.12 and PHP 5.2.10
I'm running a couple of different websites, using wordpress so here's the problem.

When trying to access [www.example.com](www.example.com) (from anywhere outside my local network) the browser wants to download the php file. - According to google, it means that Apache is not parsing the php file before delivering to the browser.

When going to [www.example.com](www.example.com) from INSIDE my network everything works as it should.  

I have a pretty standard home network, DLink router LAMP server, switches and stuff, but I don't think it has anything to do with that. As getting to the server from outside the LAN works just fine, Apache doesn't send the parsed output


Thanks for your help

---

### Post by lohertz on 2010-10-15
Don't know what happened, but I cleared the cache in my browser and it worked. I also restarted apache and everything seems back to normal.

I wonder if this has anything to do with the updates I ran the other day

hmmmmmmmmmmmmmmm

---

