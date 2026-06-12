---
title: "ubuntu 10.04 lucid lynx takes too long to boot"
date: 2010-05-22
forum: General Help
---

### Post by dragosdog on 2010-05-22
Hello everyone! This is my first post and even though I have read several posts on this issue, I still could not find a workaround to improve my startup speed. Some posts suggested to disable Floppy from BIOS but not even I don't have a floppy, but also nothing else appears in BIOS apart from my HDD and DVD drive. I installed bootchart and uploaded an image of my latest boot on imageshack:  [http://img248.imageshack.us/img248/3741/dragosdesktoplucid20100.png](http://img248.imageshack.us/img248/3741/dragosdesktoplucid20100.png) but I do not know really how to interpret it. Bare in mind that I did not use to have this problem while running Karmic...back then the OS started twice as faster as it does now after the update (now it takes at least 75 seconds to boot) . Call me crazy but I expect more from my computer given its specifications. I would greatly appreciate any help you could provide me in order to help me speed up my startup time. 

Thank you for taking the time to read this post. Have a nice day.

P.S. aside from the startup problem, ubuntu 10.04 works like a charm

---

### Post by sille777 on 2010-05-22
on my 4 year old laptop i have timed 65 seconds for booting.  Thats from power button press to wi-fi signal acquired.

A big improvement over the WinXP this laptop came with.  Seems pretty quick to me.

perhaps go to System > Preferences > Startup Applications 

And un-check a few things you may not need to start...

In my case I turned off the bluetooth this computer doesn't even have.

---

### Post by dragosdog on 2010-05-22
Hello, and thanks for your reply.. I disabled bluetooth, mysql server and Zend server (all of them being enabled on startup) and thus I managed to reduce my startup time from around 75 seconds to about 40 seconds... It is indeed an improvement but when reading some posts from the folks who entered BIOS to disable their floppys they bragged that their version of ubuntu 10.04 booted in less than 10 seconds... I uploaded an updated version of my bootchart after disabling some startup services here [http://img248.imageshack.us/img248/4890/dragosdesktoplucid20100g.png](http://img248.imageshack.us/img248/4890/dragosdesktoplucid20100g.png) ... There must be something else hogging up a big part of my memory.

The funny part is that booting in karmic was much faster than this and it certainly didn't differ much when enabling certain services to run at startup. I wonder if there is another workaround for my problem

---

### Post by SisterNotes on 2010-05-27
I am noticing a similar problem - Lucid boot is slower than Karmic. When I boot I get a black screen with a blinking cursor in the upper left corner for several seconds before the Ubuntu splash screen shows up. Then the login screen. Then after logging in several more seconds before I see the desktop. I&#7743; using a Compaq Evo N610c, which still works thanks to Ubuntu!

Can anyone explain why Lucid is taking longer than Karmic? I&#7743; not looking for a 10 sec boot, just something closer to what I had before.

---

### Post by gerowen on 2010-05-27
That's weird it's taking longer to boot for you guys, I timed mine the other day.  From the moment my BIOS screen blacks out until I get the login screen, 17 seconds.  I'll go try it out for myself, but as soon as you get to the graphical Ubuntu logo loader screen, press Esc and see if you get a verbose output of the startup process, maybe this will help you pinpoint what process is eating up all the time.  I know when I used to have Fedora you could do that.

---

### Post by sdennie on 2010-05-27
Your boot chart shows that 30 seconds are spent doing ureadahead.  ureadahead is a process that pull files into memory that it knows it's going to need during the boot to try to make it faster.  It's possible the ureadahead pack files are corrupt/wrong and that is causing it to do odd things.  That, or your disk is failing and the new installation of 10.04 happens to need some of the failing/bad sectors whereas Karmic didn't.  I would try this:

```

sudo rm /var/lib/ureadahead/*pack

```

Then reboot twice (once to regenerate those files and twice to see if it fixed the problem).

---

### Post by loath2tinker on 2010-05-31
Following sdennie's suggestion improved my boot speed notably; I'm still at 9.10, but had noticed markedly increased boot times for past ~1 week.  I'm unsure what caused my own boot time to increase.

---

### Post by abhot on 2010-06-02
@ [dragosdog]("http://ubuntuforums.org/member.php?u=956490")
this is kinda stupid but are you sure your floppy drive is disabled from the bios..
i had a similar problem , disabling floppy drive reduced my boot time from 45s->18s

recently i did a bios update on my asus p5k mobo
i don't have a floppy drive but somehow the default setting of the updated bios enabled the floppy drive

you should search for fdc controller and disable it or
in my bios there is an option called "legacy diskette A" i have no idea what it means but disabling it 
disabled the floppy drive & now my boot time has significantly reduced

hope this helps...

---

### Post by jt1 on 2010-06-02
Well I'm experiencing the same problem. I upgrade from Karmic to Lucid yesterday and the boot process now takes MUCH longer (like 2-2.5x longer). I alse have the problem with the black screen with just a cursor which stands there for over 10 s.

All this is very stupid cause the most important reason i changed form Vista to Ubuntu is that it took ages to boot up Vista. Now I have the same with Ubuntu :(

---

### Post by philinux on 2010-06-02
> **jt1 said:**
> Well I'm experiencing the same problem. I upgrade from Karmic to Lucid yesterday and the boot process now takes MUCH longer (like 2-2.5x longer). I alse have the problem with the black screen with just a cursor which stands there for over 10 s.

All this is very stupid cause the most important reason i changed form Vista to Ubuntu is that it took ages to boot up Vista. Now I have the same with Ubuntu :(

See the General Help forum sticky.

---

### Post by jt1 on 2010-06-02
> **philinux said:**
> See the General Help forum sticky.

Thanks dude! The boottime still isn't what it used to be, but at least my system is usable again!!!!

---

### Post by atulkakrana on 2010-07-24
> **sdennie said:**
> Your boot chart shows that 30 seconds are spent doing ureadahead.  ureadahead is a process that pull files into memory that it knows it's going to need during the boot to try to make it faster.  It's possible the ureadahead pack files are corrupt/wrong and that is causing it to do odd things.  That, or your disk is failing and the new installation of 10.04 happens to need some of the failing/bad sectors whereas Karmic didn't.  I would try this:

```

sudo rm /var/lib/ureadahead/*pack

```

Then reboot twice (once to regenerate those files and twice to see if it fixed the problem).

I did exactly as you said...YOU ROCK DUDE....I knew that the problem was due to 'uread' but didnt knew about how to solve it....THANKS AGAIN

I confirm this fix and recommend higly!

But I believe that I have to do it everytime I install or Uninstall anything. I will post update over this issue soon.

---

### Post by Nathroq on 2010-07-30
Hello! I was searching for an  answer to the same problem, i&#7743; new to linux and Ubuntu 10.04 is the first distro I use. Did as  said,  entered bios and disabled floppy, but it takes around 75 secs. I'm attaching muy bootchart, its pretty messy,  i dont understand much, can anybody help me please???

_[http://img64.imageshack.us/img64/1636/natalielaptoplucid20100.png](http://img64.imageshack.us/img64/1636/natalielaptoplucid20100.png)_



THANKS A LOT for ur time!

---

### Post by Nathroq on 2010-07-30
Sorry, forgot picassa may get pic compressed... here is in imageshack

[http://img64.imageshack.us/img64/1636/natalielaptoplucid20100.png](http://img64.imageshack.us/img64/1636/natalielaptoplucid20100.png)

---

