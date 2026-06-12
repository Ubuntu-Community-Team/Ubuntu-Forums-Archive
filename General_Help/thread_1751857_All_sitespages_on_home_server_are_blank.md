---
title: "All sites/pages on home server are blank"
date: 2011-05-07
forum: General Help
---

### Post by galileo005 on 2011-05-07
I installed ubuntu 10.04 and setup webmin & phpmyadmin on my server at home. After a bit of tweaking to the virtualhosts everything was working. When I went to use it again the other night all the sites, phpmyadmin & webmin were just blank pages.

I did a bit of searching for a solution, and the first thing I came across was an automatic update to the kernal, so I tried to boot from an old one but that didn't work (although I'm sure I did that properly)

Then I asked a friend and he suggested that it might be an automatic update to a php or apache config file. How do I check if/when a file was updated and can I revert to an old one?

All I'm seing in my apache2 error log is:
[notice] caught SIGTERM, shutting down
[notice] Apache/2/2/14 (ubuntu) PHP/5.3.2-1ubuntu4.8 with Suhosin-Patch configured -- resuming normal operations
When I restart apache

Or is this likely to be some other cause?

Edit: I didn't notice before but while the page were blank, I couldn't see my server on my network. I restarted it and then it appeared on my network and everything worked again. Seems like I need to boot up my networked computers before my server??

---

