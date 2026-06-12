---
title: "Paypal IPN"
date: 2011-03-06
forum: General Help
---

### Post by ks07 on 2011-03-06
Hey all,

I'm currently running a website that accepts paypal donations from users to support the site. I'm in need of an IPN script (been looking for PHP, but anything that will run on an Ubuntu Server w/ apache is fine) that handles the IPN process and inserts the information received into a mysql table. I've tried a few different scripts I've found across the web, but have had no luck using them with the developer sandbox's simulator. Does anybody have any recommendations?

Thanks

---

### Post by MicahCarrick on 2011-09-10
Did you ever get this working?

I wrote a paypal IPN script 6 years ago that's been pretty popular and just released a rewritten IPN listener script for PHP 5 which is even better. You can have it use cURL or fscokopen depending on your server configuration and can also switch between HTTP and SSL. 

If you have any trouble with it get in touch with me and I'll help you get it working.

Quick example is available with the source code on Github: [https://github.com/Quixotix/PHP-PayPal-IPN]("https://github.com/Quixotix/PHP-PayPal-IPN")

---

