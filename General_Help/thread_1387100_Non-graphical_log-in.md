---
title: "Non-graphical log-in"
date: 2010-01-21
forum: General Help
---

### Post by kamaji792 on 2010-01-21
Hi all,

Is there any way I can have a non-graphical log-in?

I'm quite happy to log-in in a terminal and then start gnome after.

The reason I want to do this is my system as it boots seems to think that the screen is 1600 pixels wide and so I loose the display until I get to the log-in screen (I've worked out how to stop the log-in screen running at 1600).

I like the old way of logging in watching all the systems coming up reporting OK or Failed.

Any help greatly appreciated.

---

### Post by zollie on 2010-01-21
you really should search for this type of stuff, man.

forums and the interwebs are FULL of this info

[http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/)

---

### Post by kamaji792 on 2010-01-21
Thanks for the reply zollie.  Sadly the command it suggested, which is repeated in several other places, does not work.

I tried:

```
sudo update-rc.d -f gdm remove
```

When I re-boot it still boots graphically.

Interestingly I don't get any of the output your site suggest I should.

Thanks anyway.

Need to write some PHP so time to stop playing.

---

### Post by kamaji792 on 2010-01-21
Further research revealed a utility **rcconf**.

I installed it and ran it.

It shows me that **gdm** has been disabled but I still get a graphical log-in.

The really funny thing is my system did and update while I was playing and needed to restart so I let it and now my problems have gone away.

I just have to work out why the system wants to check the filing system each time it boots.

---

### Post by kamaji792 on 2010-01-21
OK I found a solution.

> **iscatel said:**
> well, this disables sound, as a previous post pointed out, but here goes:

in /etc/default/grub, comment out 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

add

GRUB_CMDLINE_LINUX_DEFAULT="text"

then

sudo update-grub

this will pass "text" on the kernel line, disabling gdm.

Here is the [link to the thread](http://ubuntuforums.org/showthread.php?t=1305659&page=3)

It did kill my sound though :/

---

