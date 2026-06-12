---
title: "Unexpected logout / x.org segfault when using Gimp, always reproducible"
date: 2012-07-05
forum: General Help
---

### Post by MrFogg on 2012-07-05
Hello everyone...

I am experiencing a rather weird problem I have never encountered before. While using Gimp, the system will **abruptly** log out. 

For example:  Open Gimp > New File > select bucket tool (or any tool) > (click) on the new image with tool... then, BOOM! The system logs out. 

I am using Precise 12.04, and I have a Thinkpad T420s.  The only logs that have any information about the abrupt logout are what I found in:

/var/log/Xorg.0.log.old,

```
Backtrace:
[   226.575] 0: /usr/bin/X (xorg_backtrace+0x26) [0x7fddaa92b996]
[   226.575] 1: /usr/bin/X (0x7fddaa7a3000+0x18c83a) [0x7fddaa92f83a]
[   226.575] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fdda9ac9000+0xfcb0) [0x7fdda9ad8cb0]
[   226.575] 3: /usr/bin/X (0x7fddaa7a3000+0x5e71a) [0x7fddaa80171a]
[   226.575] 4: /usr/bin/X (0x7fddaa7a3000+0x58070) [0x7fddaa7fb070]
[   226.575] 5: /usr/bin/X (0x7fddaa7a3000+0x1230ef) [0x7fddaa8c60ef]
[   226.575] 6: /usr/bin/X (0x7fddaa7a3000+0x4e8b1) [0x7fddaa7f18b1]
[   226.575] 7: /usr/bin/X (0x7fddaa7a3000+0x3d6da) [0x7fddaa7e06da]
[   226.575] 8: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fdda895e76d]
[   226.575] 9: /usr/bin/X (0x7fddaa7a3000+0x3d9d1) [0x7fddaa7e09d1]
[   226.575] Segmentation fault at address 0x28
[   226.575] 
Caught signal 11 (Segmentation fault). Server aborting
[   226.575] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[   226.575] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```

and .xsession-error.old

```
(gimp-2.6:7435): LibGimpBase-WARNING **: gimp-2.6: gimp_wire_read(): error
```

This error is always reproducible, I log back in open gimp, use a tool, **BAM**! logout again...!?

Can anyone help me capture more error information so that it can be attached to this thread?  

Maybe it could be a bug? Any help from the community is greatly appreciated since I need to use Gimp to make a meager living...

---

### Post by flemur13013 on 2012-07-05
[FONT=monospace]> gimp-2.6:7435

Maybe update to 2.8; it's in the repositories.  It's a bit different, but better.

[/FONT]

---

### Post by tranduyhung on 2012-07-06
I have a similar problem with my Dell Inspiron 14R 5420 when I try to crop my images.

I will try gimp-2.8 to post the result here. Thank you!

---

### Post by Gyalogtank on 2012-07-06
I have the same problem on my Dell Inspiron N5110, using Ubuntu 12.04. 

I used Gimp three or four days ago, then nothing was wrong with it, I have not changed anything on my system since then, I have not installed a single program. 

Maybe Gimp got a bad update in the past week? Anyone knows anything?

---

### Post by tranduyhung on 2012-07-06
I installed gimp 2.8 from ppa:otto-kesselgulasch/gimp
The problem was gone!!!
Thanks flemur13013 for your suggestion!

---

### Post by Gyalogtank on 2012-07-07
Gimp 2.8 seems to be working fine. I guess this is the solution then. 
I have followed this how-to guide:
[http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html)

---

### Post by biji on 2012-07-08
shocked... when trying to click gimp window.. whole X server crashes....... :(
will try new gimp
:lolflag:

---

### Post by EdgarPE on 2012-07-10
Same here. Gimp was fine a couple of days before, now unexpected logout when clicking on the image with every tool.

System:
Dell Latitude E6420
Ubuntu 12.04 64bit (8GB ram)
Gnome 3 desktop
GImp 2.6.12

---

### Post by dtstanton on 2012-07-11
I've had the problem since yesterday. Precise 12.04, Gimp 2.6.
 
Tried to install 2.8, but it keeps giving me 2.6 even after removing Gimp and purging it, then getting the PPA and installing what's supposed to be 2.8.
 
I don't really want 2.8, but if 2.6 isn't going to work any more I don't have any choice.
 
What am I missing or doing wrong?
 
Thanks,
   -Dale
 
[I](Follow-up edit:
I was finally able to re-install 2.6 after a few rounds and re-booting, and it's working ok now.[/I])

---

### Post by blue luke on 2012-07-12
Hi everyone,

I'm also suffering from this bug and it seems that I'm not alone here ;-)

There's already a bug report at lauchpad:

**[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1021517](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1021517)**

Right now, only 3 people there (including me) have confirmed that they are affected by our problem. In order to get some attention by the developers,
more affected users will certainly help our cause.

So if you are sure that you have the same problem (check your XorgLogOld.txt in /var/log after a crash and compare it to the one posted at launchpad),

 please[B] vote "This bug affects 3 people. Does this bug affect you?" at the launchpad site.
[/B] 
You can do that by logging into your launchpad (or Ubuntu One) account and clicking on that text. 
(Registrating an account takes less than a minute, so it really shouldn't be a problem in case you don't have one already)

Thanks,
Luke

---

