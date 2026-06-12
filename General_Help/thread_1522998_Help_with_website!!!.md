---
title: "Help with website!!!"
date: 2010-07-02
forum: General Help
---

### Post by aala on 2010-07-02
Hi everyone!

 I'd like to know If anybody knows about a open source php comments box that I can use on my website.

You guys know, something dynamic,... and that it posts the input of the comments instantly.

Any suggestions??? Every comment welcome,...

Thanks!... oh and by the way I heard about drupal, and joomla, but I was looking for something more simple.

---

### Post by 4Orbs on 2010-07-02
If your website already exists and you just want to add a third party (offsite) guestbook, there are plenty of places like bravenet.com that provide the service. With these you only need add a small bit of code (actually just a link) on your existing pages.

If you want something that is really part of your own website, then you will need your site to be running from a database (sql or others) in order to get the instant, dynamic updating of comments. Since you already know about drupal and joomla... then I assume you already know about Wordpress which is probably the most basic and easiest-to-use cms available. But it is an entire website software, not just an add-on.

---

### Post by stderr on 2010-07-03
Not necessarily the best advice here, but my approach with these sort of things is to just code it. It doesn't take long to set up a MySQL DB, and wouldn't take very long either to write some PHP to update the DB and an AJAX-ish updater. Possibly quicker than trying to find a good existing solution and integrate it... Plus, when you've coded it yourself, it's dead easy to customise.

On the other hand, one could think of it like this: I am essentially recommending that you re-invent the wheel. And the axle. *shrug* - works for me...

I should add, I started building a site with Joomla for the first time a week ago, and whilst it would have taken me ages to build such an advanced CMS, Joomla is seriously impeding my progress in other areas.

---

### Post by Spr0k3t on 2010-07-03
Well put stderr.  If you build it yourself, you could customize it to no end.  There are several examples that already exist as plugins for other many of the open source CMS systems available.  Just look up things like shoutbox, guestbook, etc and you should find several sources to build your own system.

When you build your own, make sure you remove the server side code from the final product.  That way you can modularize your source and offer it out in GPL fashion.  I have an old guestbook example, but nothing with ajax and required refreshing.  Really really easy to code.  My only suggestion would be to incorporate some form of captcha.

---

### Post by aala on 2010-07-03
Thanks to everyone, your help were excellent!...

It's done!

---

