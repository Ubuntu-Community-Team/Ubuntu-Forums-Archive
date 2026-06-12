---
title: "picolcd 256x64 not working in Ubuntu 10.04"
date: 2010-07-26
forum: General Help
---

### Post by HwyXingFrog on 2010-07-26
I have been using my picoLCD 256x64 display for quite a while in Ubuntu 9.10, I recently upgraded to Ubuntu 10.04 and it stopped working, I tried reinstalling and still didn't work.

I then decided I would do a much needed complete install to Ubuntu 10.04 64Bit (I had been running 32 bit), and I'm still unable to use my picoLCD

When I run the command to start the LCD

```
~/picolcd-256x64/picoLCDGraphic/start-picolcd256x64.sh ~/picolcd-256x64
```

I get these errors:

```
Installation path: /home/user/picolcd-256x64
Running gksu wrapper
/home/user/picolcd-256x64/picoLCDGraphic/gksu: error while loading shared libraries: libstartup-notification-1.so.0: cannot open shared object file: No such file or directory
/home/user/picolcd-256x64/picoLCDGraphic/gksu: error while loading shared libraries: libstartup-notification-1.so.0: cannot open shared object file: No such file or directory
```

Any help is appreciated, thanks.

---

### Post by jonathansfl on 2010-10-27
We are having a similar problem. Have you figured this problem out yet?

---

### Post by aeiah on 2010-10-27
well, you're missing libstartup-notification-1.so.0 as the error says.. this may be missing, or, as is sometimes the case with these things, the naming of it has changed and you simply have to create a symbolic link from the file that exists over to libstartup-notification-1.so.0


perhaps the picololcd source, if available, will give more details
[http://www.picolcd.com/drivers/](http://www.picolcd.com/drivers/)
the source README says all documentation is on [http://ssl.bulix.org/projects/lcd4linux/](http://ssl.bulix.org/projects/lcd4linux/)

following the howto on there might give you something useful

---

### Post by airtonix on 2010-12-05
you need to compile the source package provided on the picoLCD driver website.

---

