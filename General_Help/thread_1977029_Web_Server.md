---
title: "Web Server"
date: 2012-05-09
forum: General Help
---

### Post by bOgNeR17 on 2012-05-09
Hello I am running the latest version of Lubuntu and I am wondering is there anyway possible that I could setup a web hosting server that my web clients could host their websites on it along with a control panel etc similar to cpanel.

---

### Post by bOgNeR17 on 2012-05-10
Anyone?

---

### Post by wfong on 2012-05-14
Hello,

There are a lot of aspects to web hosting that you may not have considered. You may want to look into using Ubuntu Server LTS, as Lubuntu is generally used for desktops. 

Can you describe what you're thinking about offering? Why not use existing services out there?

-will

---

### Post by na5h on 2012-05-14
A [LAMP]("http://en.wikipedia.org/wiki/LAMP_(software_bundle)") server is probably the easiest and most convenient to set up...there are plenty of tutorials out there on how to do it. Here are a couple that I found on Google (I haven't read them through thoroughly):
[http://gregrickaby.com/2011/10/how-to-install-lamp-on-ubuntu.html](http://gregrickaby.com/2011/10/how-to-install-lamp-on-ubuntu.html)
[http://www.lamphowto.com/](http://www.lamphowto.com/)

Please be advised that if you intend to set up a "real" web hosting server with real clients who pay real money, there are many questions regarding for instance, backup and security that must be accounted for. If you do not know how to set up a server on your own, then I definitely do not recommend that you try to set up a web hosting service!

---

### Post by Lars Noodén on 2012-05-14
All you need to set up web hosting is to add a web server like Apache2 or nginx.  If you're going to serve several sites off of the same machine, which is a good idea, then you'll want to set up a separate [Virtual Hosts](https://httpd.apache.org/docs/2.2/vhosts/).  

Each Virtual Host will need its own Document Root.  And you'll probably need to set up group level permissions for you users to be able to edit their own web server, but not others.

---

