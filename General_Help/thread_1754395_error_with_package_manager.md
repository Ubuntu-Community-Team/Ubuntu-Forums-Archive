---
title: "error with package manager"
date: 2011-05-10
forum: General Help
---

### Post by TeeRoy32 on 2011-05-10
HI every time I update or install a package i get an error, it has happened since I tried to follow these instructions on a website to compile my own kernel, whilst it was installing required packages kexec-tools had an error.

The package manager keeps spitting this at me
E: kexec-tools: subprocess installed post-installation script returned error exit status 2
all my updates work, and my apps work too, but every time I get that error.
Its more annoying than anything else. Oh and I've given up on compiling my own kernel so I don't need exec-tools so I'd love to clean it up

cpu = 3.4 ghz pentium 4
ram = 2gb
graphics = G6600 256mb ram
stock intel board
80gb sata drive
Ubuntu 10.04 Lucid Lynx 64bit

---

### Post by JDShu on 2011-05-10
Sounds like a dpkg error, a quick search I found this: 

[http://www.pixelshine.net/howto/2011/02/21/fixing-subprocess-installed-post-installation-script-returned-error-exit-status-2/](http://www.pixelshine.net/howto/2011/02/21/fixing-subprocess-installed-post-installation-script-returned-error-exit-status-2/)

Why it happened is worrying though... did anything happen while you were installing the package? Perhaps a hard reset or something?

---

### Post by TeeRoy32 on 2011-05-10
I had just installed a humble bundle game under wine, whilst my terminal was downloading and installing all the packages for compiling a kernel I started the game up and it made the computer hang for a bout 10 seconds and wine crashed. Which happens on that game every time I try and load it, its Trine by the way, I tried the linux file but it just opens up a terminal and crash's, any how thats for another thread. I'll have a look at your link, have a crack at it and will let you know

---

### Post by TeeRoy32 on 2011-05-10
I went to that link and followed the instructions and the errors now gone away thank you very much

---

