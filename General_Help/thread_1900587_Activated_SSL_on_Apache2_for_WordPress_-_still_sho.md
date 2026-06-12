---
title: "Activated SSL on Apache2 for WordPress - still shows red lock"
date: 2011-12-26
forum: General Help
---

### Post by houmank on 2011-12-26
Hi,

I have installed a WordPress successfully.

I have copied the offical CA SSL certificates chasebot.com.crt and gd_bundle.crt via SSH to my server and set everything up.

Now when I go to the login page

[https://www.chasebot.com/wp-login.php]("https://www.chasebot.com/wp-login.php")

I still get a red lock, when you click on it, it says the identity of the website has been verified by Godaddy and the connection is encrypted with 256Bit. 

However this page includes resources that are not secure and an attacker could take advantage of it etc.

Back then on IIS7.5 I didnt get that with Wordpress, have I missed something on Apache2 to setup?

Many Thanks,
Houman

---

### Post by houmank on 2011-12-26
Ok now after 10 minutes, its all green in Chrome.  Weird. Is there some kind of delay involved for SSL certificates to be activated? Didn't know that. 

Finally its all working.  I must say its incredible how fast everything is on Ubuntu.  When I click around in WordPress settings everything works instant. No tiny delays as it was the case with IIS7.5.

It feels very solid. :guitar:

---

