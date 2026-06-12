---
title: "Amor MD2 on Ubuntu? compile issue"
date: 2009-07-15
forum: General Help
---

### Post by doobiest on 2009-07-15
Hey guys I'm trying to get Amor MD2 running on ubuntu. I know this app is dated (2004) but it's cool.. If you're familiar with Amor in the ubuntu repositories, this is a similar program but it creates desktop characters out of quake2 models.

As far as I'm concerned it's way cooler than the original amor app. Don't know why there wouldn't be a binary in the repo.

Annyway there's a link to the source at the bottom of my post. I'm having issue compiling. this is what I get.

```

...
checking for libXext... yes
checking for Xinerama... no
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

```

Best I can tell I have qt3 dev packages and the headers already installed.  Maybe I need to explicitly state where they are??  I don't know, I'm not a source code champ.

[http://www.2robots.com/2004/01/30/amor-md2/]("http://www.2robots.com/2004/01/30/amor-md2/")

Thanks.

---

