---
title: "You Tube videso don't play"
date: 2009-10-12
forum: General Help
---

### Post by daldude on 2009-10-12
When  I visit You Tube the videos don't play. When I click on a video thumbnail to play it it gives me a message "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player" with a link to download the flash player so I select deb for umbuntu 8.04+ and download it and then try to install it but it and the installer gives me the message "Error wrong architecture 'i386'." I'm useing the 64bit version of Ubuntu 8.04 released in April 2008.

How Do I get Youtube Videos to play?

---

### Post by coldReactive on 2009-10-12
In Programs/Applications > Accessories > Terminal

```
sudo apt-get install flashplugin-nonfree
```

Restart Firefox afterwards.

---

### Post by Johnny B on 2009-10-12
use this guide:
[http://ubuntuforums.org/showthread.php?t=1233235]("http://ubuntuforums.org/showthread.php?t=1233235")

---

### Post by coldReactive on 2009-10-12
> **Johnny B said:**
> use this guide:
[http://ubuntuforums.org/showthread.php?t=1233235]("http://ubuntuforums.org/showthread.php?t=1233235")

You don't need 64-bit flash to play youtube videos.

---

### Post by daldude on 2009-10-12
After I screwed up Ubuntu by installing a bunch of programs with the all open source applications option in add remove selected I had to reinstall so I installed the 32-bit to avoid the hassle of trying to get Flash to work in the 64bit version of Ubuntu but thanks for the info any way. I can use it if I decide to install the 64bit version again but I might install 9.04 64-bit if Adobe has support for that without having to install it manually by typing  all those commands in a  terminal window.
Unix command prompts are a lot more complex then windows command prompts and I still don't understand the directory Structure in Unix.:)

---

### Post by meka4996 on 2009-10-18
... it's better to install everything in 32 bit, even if you have a 64 bit machine, as there are something missing in 64 bit depository like drivers, codecs,...

---

### Post by coldReactive on 2009-10-18
> **meka4996 said:**
> ... it's better to install everything in 32 bit, even if you have a 64 bit machine, as there are something missing in 64 bit depository like drivers, codecs,...

There is a w64codecs package in medibuntu: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

granted it doesn't play some Windows Media Files, and some AVI files.

---

### Post by ikt on 2009-10-18
> **meka4996 said:**
> ... it's better to install everything in 32 bit, even if you have a 64 bit machine, as there are something missing in 64 bit depository like drivers, codecs,...

negative.

I currently install everything in 64 bit if possible and have no such issues.

64 bit flash player works 100% better than the wrapper based 32 bit flash in 64 bit windows, that said it still doesn't go full screen but that is adobes fault.

---

