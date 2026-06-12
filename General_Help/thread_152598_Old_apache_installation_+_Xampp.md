---
title: "Old apache installation + Xampp"
date: 2006-03-30
forum: General Help
---

### Post by SreckoMicic on 2006-03-30
Problem is > I installed Xampp, started ok. Before that deleted completly my old Apache installation.
But when I type in browser "localhost", it's display me "Placeholder page" that was displayed with old version of Apache, not xampp intro page. I even deleted var/www/index.html, what was that placeholder page but browser display me that page again.
Why, something with configuration, or what?????
SOLVED --- > Solution was so stupid that I'm not going to even tell you :-)

---

### Post by Soyle Mycelf on 2006-10-20
Reviving this thread as I am having the same problem in reverse: Installed xampp and it worked fine.  Decided I wanted more control so I installed apache2.  When I go to [http://localhost](http://localhost) I get a 404 The requested URL /xampp/ was not found on this server.  If I manually type in the exact files I want under /var/www (apache2's htdocs dir) I get what I want, so I know I am using  the correct .conf file.

I have looked in the apache2.conf file, made sure my /etc/init.d/apache2 startup uses the apache2 install and not the xampp, and scoured the mods/sites-available for any reference to xampp.  Does anyone have any clue what is going on?  What is the detailed process used to route an incoming request to determine where to look for the htdocs?:confused: ](*,)

---

