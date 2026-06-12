---
title: "encryption like Fedora"
date: 2009-12-09
forum: General Help
---

### Post by DouglasAWh on 2009-12-09
I run a small deployment of Linux laptops and due to some new laws, we are going to have to start requiring encryption.

I want Ubuntu to work like Fedora does in this regard.  You can see what I mean at 

[IMG]http://farm3.static.flickr.com/2533/4172339849_2a15e28c00.jpg[/IMG]

larger image available at [http://www.flickr.com/photos/dawhitfield/4172339849/sizes/o/](http://www.flickr.com/photos/dawhitfield/4172339849/sizes/o/)

The alternative is to let me know how to encrypt users home dirs.  I can do this easily at boot in Ubuntu, but I want this to happen for *all* new users too.  I need something scriptable if it's not full-disk.

Thanks!

---

### Post by bodhi.zazen on 2009-12-09
You can do the same thing (LUKS) with Ubuntu , but not from teh desktop CD, you need to use the alternate CD.

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

It is written for 8.04, but it is essentially the same with all higher versions of Ubuntu.

---

### Post by DouglasAWh on 2009-12-10
ok, this is going to work, but now I have to script auto-login for users. Should I start a new thread?

---

### Post by bodhi.zazen on 2009-12-10
> **DouglasAWh said:**
> ok, this is going to work, but now I have to script auto-login for users. Should I start a new thread?

GDM can be set to auto login. Otherwise, yes, people would not see your request for assistance with a script on this thread.

---

### Post by DouglasAWh on 2009-12-10
> **bodhi.zazen said:**
> GDM can be set to auto login.

Yeah, already done that through the GUI, but we don't want to go through the GUI with every new user.

I'll start a new thread after doing a little bit of research.

---

