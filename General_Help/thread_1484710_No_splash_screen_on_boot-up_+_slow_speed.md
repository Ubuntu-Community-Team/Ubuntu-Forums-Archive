---
title: "No splash screen on boot-up + slow speed"
date: 2010-05-16
forum: General Help
---

### Post by Eremis on 2010-05-16
Hi Everybody!

Hi, I just installed ubuntu 10.4 on my new laptop and when it boots up there is no splash screen (All I see is a blinking cursor) and it takes about 28 seconds to boot up...

Does anybody know how to fix this?

BTW I do have all the graphic stuff working...

Thanks...

---

### Post by kio_http on 2010-05-16
```
sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash  && sudo update-initramfs -u                      
```This will introduce a 1/2 second boot delay which give time for the graphics module to load so that you can see the splash.
Installing the Ubuntu updates could speedthings up.

---

### Post by Eremis on 2010-05-17
I can see the splash now, but its very pixilated...
Is that how it should look?

---

