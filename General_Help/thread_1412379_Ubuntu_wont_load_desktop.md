---
title: "Ubuntu wont load desktop"
date: 2010-02-21
forum: General Help
---

### Post by ornashmena on 2010-02-21
Hi,

Few days after installing Ubunto 9.10, during installation of gstreamer, 
the installation utility got stuck, and with it the whole desktop icons. 
(I think the gstreamer has nothing to do with it).
When I tried to execute some icon, like the terminal, it will not open.
After restarting the computer, I get a tty1 login terminal and not the graphical one (tty7).
When pressing Ctrl+Alt+F7, nothing happens.
It switches to a black screen.
"sudo startx", gives some error log.

I already reinstalled the X-server, ubuntu desktop and other stuff.

What can be the problem?
Is it related to my video card (nvidia 7600 GT)?
I didn't install any nvidia specific driver.

This happened to me earlier and I reinstalled Ubunto.
I think maybe I should move to some other distribution.

Thanks.

---

### Post by NightwishFan on 2010-02-21
If you can make it to a command line run (exactly as posted or one command at a time without the &&):
```
sudo aptitude update && sudo aptitude install ubuntu-desktop && sudo apt-get -f install
```

---

