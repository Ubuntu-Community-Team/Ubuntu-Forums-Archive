---
title: "Software suggestion needed for virtual tour creation software"
date: 2011-05-12
forum: General Help
---

### Post by nagarajan_s on 2011-05-12
I can use Hugin Panorama to stitch the paorama image JPEG.

Are there any software available for Ubuntu which can take the jpeg and create a interactive panorama (or)virtual tour (in flash, QT or any other interactive format) ?

Thanks for your help

---

### Post by dragonfly41 on 2011-05-12
Gimp Pandora plugin also stitches together images.

...

You can write your own interactive flash app with open source.

Install tomcat6 servlet and jsp engine through ubuntu software centre

there are six packages to select
tomcat6
tomcat6-common
tomcat6docs
tomcat6-admin
tomcat6-examples
tomcat6-user

see .. 

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

[http://www.blog.highub.com/jsp/jsp-core/install-and-configure-tomcat-on-ubuntu/](http://www.blog.highub.com/jsp/jsp-core/install-and-configure-tomcat-on-ubuntu/)



check that the tomcat server launches with [http://localhost:8080](http://localhost:8080)

download openlaszlo 4.9.0 servlet

[http://www.openlaszlo.org/download](http://www.openlaszlo.org/download)

Dev Kit any OS

[http://download.openlaszlo.org/4.9.0/openlaszlo-4.9.0.war](http://download.openlaszlo.org/4.9.0/openlaszlo-4.9.0.war)


copy openlaszlo-4.9.0.war into tomcat webapps folder

/var/lib/tomcat6/webapps/

shut down and restart tomcat6 server

go to [http://localhost:8080/openlaszlo-4.9.0/](http://localhost:8080/openlaszlo-4.9.0/)

Start writing your virtual tour app in openlaszlo code.

---

### Post by nagarajan_s on 2011-05-13
@ dragonfly41 : Thanks for the suggesstion. While I am inclined to (in fact, I will in the future) try out Laszlo platform here, I think, it will be a lot more involved task to write a virtual tour app myself. 

Are there any such app out there like this Tour weaver([http://www.easypano.com/virtual-tour-software.html](http://www.easypano.com/virtual-tour-software.html)) for open source software _users_? :)

I heard there are a few java based apps that should work on Linux as well.

Any help is much appreciated.

---

### Post by dragonfly41 on 2011-05-13
Might be easier for you to purchase a package ..

[http://krpano.com/](http://krpano.com/)

---

