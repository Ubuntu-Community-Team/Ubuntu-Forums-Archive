---
title: "clock or time synch problems, check the image!"
date: 2009-11-08
forum: General Help
---

### Post by Hoaxe on 2009-11-08
hey, can anyone help me fix this?
see the time at the top doesn't match the time at the bottom!

---

### Post by munky99999 on 2009-11-08
You have your location set to where ever. Which can be different from the time that is set.

Rightclick the clock. Goto properties. Then locations. Then adjust the location to be in the correct timezone.

Click time settings at the bottom of properties to change the time if that's what is off.

---

### Post by Hoaxe on 2009-11-08
> **munky99999 said:**
> You have your location set to where ever. Which can be different from the time that is set.

Rightclick the clock. Goto properties. Then locations. Then adjust the location to be in the correct timezone.

Click time settings at the bottom of properties to change the time if that's what is off.

the location there is actually correct, but i deleted it and re added it, still no dice, new screenshot!

---

### Post by munky99999 on 2009-11-08
Have you tried removing the location entirely? 

The other thing that might be making the time so wonky. Could be your bios time is set wrong.

Other question might be. Did you set it up for internet time syncing in an older ubuntu

You can try

dpkg-reconfigure tzdata

personally I havent done that in awhile. Should be self-explantory in the terminal.

---

### Post by Hoaxe on 2009-11-08
> **munky99999 said:**
> Have you tried removing the location entirely? 

The other thing that might be making the time so wonky. Could be your bios time is set wrong.

Other question might be. Did you set it up for internet time syncing in an older ubuntu

You can try

dpkg-reconfigure tzdata

personally I havent done that in awhile. Should be self-explantory in the terminal.

did both, and yes i'm up for time sync.

this problem happened on upgrade, but i'll try the bios one as well some time. as for `dpkg-reconfigure tzdata`

it returned this:

```
Current default timezone: 'America/Montreal'
Local time is now:      Sun Nov  8 20:49:53 EST 2009.
Universal Time is now:  Mon Nov  9 01:49:53 UTC 2009.

```

clearly what i want to fix is universal time.

---

### Post by munky99999 on 2009-11-08
> **Hoaxe said:**
> ```
Current default timezone: 'America/Montreal'
Local time is now:      Sun Nov  8 20:49:53 EST 2009.
Universal Time is now:  Mon Nov  9 01:49:53 UTC 2009.

```

clearly what i want to fix is universal time.
That'd be your bios. Also since you've be upgrading since hardy I suspect. You've discovered one of those lingering little issues that ubuntu has tried to fix because microsoft wont fix itself.

---

### Post by Hoaxe on 2009-11-09
> **munky99999 said:**
> That'd be your bios. Also since you've be upgrading since hardy I suspect. You've discovered one of those lingering little issues that ubuntu has tried to fix because microsoft wont fix itself.

nope, that didn't do it. The bios time is correct, it's just the universal time that's wrong.

I read some stuff here:

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/421566](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/421566)
[http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html](http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html)

and i tried to set my universal time to my local time but no dice. 

is this a problem with one of the sh script files that have to do with the time?

r.d.

---

### Post by Hoaxe on 2009-11-10
this got fixed by removing the applet from the panel and putting in a new one -_-"

---

