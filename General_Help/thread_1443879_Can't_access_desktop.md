---
title: "Can't access desktop"
date: 2010-03-31
forum: General Help
---

### Post by apricimo on 2010-03-31
Hello,

         I just downloaded Ubuntu on my Mac using VMware Fusion and after the install I get to a screen that basically resembles DOS, it doesn't take me to the desktop. I was wondering how do I get to the desktop?

basically I have a command line that looks like...

"yoshus@ubuntu $:" 

yoshus is me of course

or something close to that and I guess I need to direct it to go to the desktop but how? 

HELP!

---

### Post by lisati on 2010-03-31
Which version of Ubuntu did you download? 9.04, 9.10, 10.04 beta, desktop, server?

---

### Post by apricimo on 2010-03-31
Well when I came to the site I was able to download only one version, namely 9.10.desktop..

I did not see a link for any other versions... is that a problem you think and if so how do I find the other version... I looked and it didn't direct me to anything else... 

thanks

---

### Post by francescogondolin on 2010-03-31
Try writing

xstart

---

### Post by burton247 on 2010-03-31
try typing 
```
startx
```

see if anything will start. That should start the X environment

or even 
```
init4
```

If it doesnt work you could just install one on top, xorg ubuntu-desktop etc

or try a different ISO [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) that should take you to the right place

---

### Post by apricimo on 2010-03-31
well startx did not work... but... I reinstalled ubuntu (btw typing within ubuntu) using VMware fusion and the difference being I installed it without using the "easy install" feature... Works great... AWESOME...

---

