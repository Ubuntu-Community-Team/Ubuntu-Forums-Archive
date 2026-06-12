---
title: "Service Oriented Architecture with Ubuntu"
date: 2012-02-21
forum: General Help
---

### Post by Arukas on 2012-02-21
Hello-

I've been studying Service Oriented Architecture (SOA).  I'd like to setup a mini project in Ubuntu using SOA.  Are there tools I could be using.  Everything I've read so far, is a high level abstraction and I'd like to make a program work.

Granted the program is going to be really simple, but I want to see if I can get it too work.  

Any help would be appreciated, even a point in the right direction.
Thanks!

---

### Post by dragonfly41 on 2012-02-22
You could install LAMP stack and setup a PHP5 SOAP Server

[http://www.lornajane.net/posts/2008/PHP5-Soap-Server](http://www.lornajane.net/posts/2008/PHP5-Soap-Server)

and look at _[http://www.w3schools.com](http://www.w3schools.com)_ for tutorials.

e.g.   [http://www.w3schools.com/soap/default.asp](http://www.w3schools.com/soap/default.asp)


[EDIT]

You'll also find this useful to understand *.wsdl content ..

[http://tomi.vanek.sk/index.php?page=wsdl-viewer](http://tomi.vanek.sk/index.php?page=wsdl-viewer)


also you might install Fiddler and Fiddler add-on in Firefox to inspect data flow between client and server


Correction .. there is no Fiddler for ubuntu ... only Windows ...

[http://www.fiddlertool.com/Fiddler2/version.asp](http://www.fiddlertool.com/Fiddler2/version.asp)

but I guess it might run in wine.   You can get by without it.

This old thread suggests nettool instead of Fiddler

[http://ubuntuforums.org/showthread.php?t=446758](http://ubuntuforums.org/showthread.php?t=446758)


[http://neilja.net/nettool/index.html](http://neilja.net/nettool/index.html)

---

### Post by Arukas on 2012-02-22
Thanks, that looks like it will take me in the right direction.

---

