---
title: "Dell Laptop lid problem"
date: 2006-02-15
forum: General Help
---

### Post by pronto185 on 2006-02-15
I have a Dell Inspiron 8200
when I close then lid, then open it again, the screen will just stay off, and I have to cut the power to do anything. It has always been that why with linux

in the devie manager it shows up as lid switch

---

### Post by nanotube on 2006-02-15
probably it just goes to sleep when you close the lid. try pressing the power button once after you open the lid to wake it up?

---

### Post by pronto185 on 2006-02-15
I have tried that nothing, Ill try it again now though
nope, no luck, i hit the power button quickly and it just turned off

---

### Post by nanotube on 2006-02-15
hey
read this forum thread, seems its talking exactly about your problem:
[http://ubuntuforums.org/showthread.php?t=120222&highlight=lid.sh](http://ubuntuforums.org/showthread.php?t=120222&highlight=lid.sh)

---

### Post by pronto185 on 2006-02-18
they never really come to a conclusion the person relized his problem was non=exsient

---

### Post by groggyboy on 2006-03-09
my apologies for restarting an old thread, but i have the same issue.  i tried reinstalling my acpi packages, but that didn't work either.  i was wondering if it had something to do with the fact that i've installed the latest intel video drivers?  or maybe my xorg.conf file is somehow f***ed?  i hope that's not the case, cuz i've had to seriously mod it to get my touchpad and tv-out working.  anyone?

---

### Post by MacV on 2006-03-09
Odd. I have the exact same laptop but whenever I close the lid, the laptop just locks the screen until i type my password. Does your laptop have a ATI or NVIDA card? Also, do you have the drivers installed for them?

---

### Post by groggyboy on 2006-03-10
my laptop is a Dell Inspiron 6000, ala the thread title.  It has an intel 915 gma card, and i'm pretty sure it has the latest drivers.  it used to lock, and required a password to resume, but now it just stays black.  hitting the power button just powers down my laptop.  i have found a bit of a workaround - i hit <ctrl><alt><F1> to switch to a console, then hit <ctrl><alt><F7> to get back to X.  maybe this will help.  (sorry about the long wait before my reply).

---

### Post by pronto185 on 2006-03-10
I just tried the <ctrl><alt><F1> , and <ctrl><alt><F7>
nothing happend after i closed and opened the lid

---

### Post by underwater on 2006-03-10
I have the inspiron 6000 as well but with ATI as the gfx card.  I don' have the problem, though my computer really doesn't do anything when I close the lid, it locks the screen but it doesn't even turn off the monitor which annoys me.  I haven't gone searching for the answer yet on how to configure it properly so there might be a really simple answer.

---

### Post by groggyboy on 2006-03-10
I know this doesn't help you, but I just gave up - i've set it to sleep (suspend-to-RAM) when the lid closes now.  not the way i'd like it to operate, but whatever. :???:

you might try commenting or uncommenting some of the options in /etc/default/acpi-support - that's how I got sleep to work.  maybe one of them will get the lid functioning properly.  you might also want to check out [http://www.ubuntuforums.org/showthread.php?t=134319&highlight=laptop+lid+blank]("http://www.ubuntuforums.org/showthread.php?t=134319&highlight=laptop+lid+blank").
it didn't work for me, but it might for you.  who knows?

cheers!

---

### Post by AndyC_772 on 2006-03-24
Press Fn-F8 to re-enable the display backlight.

---

### Post by pronto185 on 2006-03-24
thanks, that worked
but it made the screen all weird, but i fixed that by going in to command mode by pressing  crtl-alt-f1 then ctrl-alt-f7 to get out of it

---

### Post by AirIntake on 2006-08-17
Same problem here with my Dell Latitude D410. Any fix yet? I'm using Dapper though.

---

### Post by jchau on 2006-09-30
> **AirIntake said:**
> Same problem here with my Dell Latitude D410. Any fix yet? I'm using Dapper though.

[http://ubuntuforums.org/showthread.php?t=134319](http://ubuntuforums.org/showthread.php?t=134319)

Doesn't anyone search the forum before posting problems anymore?  I've had this problem solved for almost a year now.  In addition, a previous post already linked to this thread.

---

