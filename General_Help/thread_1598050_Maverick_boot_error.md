---
title: "Maverick boot error"
date: 2010-10-16
forum: General Help
---

### Post by inso_741 on 2010-10-16
I created a live usb out of the final maverick iso with the help of "Create startup disk".......It works great on my laptop but on the desktop it says "Boot error" and thers a blinkin cursor below it......specs are in my sig....please help

EDIT: all other versions ie lucid and below had no such problem!

---

### Post by VMC on 2010-10-16
> **inso_741 said:**
> I created a live usb out of the final maverick iso with the help of "Create startup disk".......It works great on my laptop but on the desktop it says "Boot error" and thers a blinkin cursor below it......specs are in my sig....please help

EDIT: all other versions ie lucid and below had no such problem!

After it gives you the error, do you see a Syslinux boot prompt. If so type 'help', without quotes, and see if it progresses.

---

### Post by kanishkdudeja on 2010-10-16
does it give you the error before installing ubuntu or after installing it ?

And is the error like:

Boot error: unknown keyword in syslinux.cfg

---

### Post by inso_741 on 2010-10-16
> **VMC said:**
> After it gives you the error, do you see a Syslinux boot prompt. If so type 'help', without quotes, and see if it progresses.

> **kanishkdudeja said:**
> does it give you the error before installing ubuntu or after installing it ?

And is the error like:

Boot error: unknown keyword in syslinux.cfg

the whole screen is black and has just 2 words:"boot error" in the top left corner....and I haven't installed it, how can I install it if it doesnt boot!!!

---

### Post by kanishkdudeja on 2010-10-16
ok..

have u created d startup disk from a previous version of ubuntu ?

if yes  

refer to 

[http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)

---

### Post by inso_741 on 2010-10-16
> **kanishkdudeja said:**
> ok..

have u created d startup disk from a previous version of ubuntu ?

if yes  

refer to 

[http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)

assuming u haven't read it already, I would like to remind you that it boots properly on my laptop...the problem is on my desktop and I've already tried removing ui

---

### Post by kanishkdudeja on 2010-10-16
oh sorry..!

---

### Post by inso_741 on 2010-10-16
alright I got it working now heres wht I did if any one has the same problem
I created live usb using "live usb creator" thats on the iso using windows
which gave me a sys linux error while then I overwrote the files using "create startup disc" from ubuntu lucid...and guess wht it finally boots on my desktop.....m testing maverick right now....my wi-fi card finally works out of the box...nice font...much attention has been given to the detail

---

### Post by lopcaf on 2010-10-19
@[inso_741]("http://ubuntuforums.org/member.php?u=731476")

I also created a usb live cd of 10.10 in 10.04 and works perfectly on a laptop (Hp mini 1100). But when I go to my desktop, i just get the "Boot error" above a blinking cursor. 

I've checked the configuration file "syslinux.cfg" for the "ui" string, but is already absent. 

Could you please describe me how did you created you usb live cd?

Kind regards

---

### Post by inso_741 on 2010-10-21
> **lopcaf said:**
> @[inso_741]("http://ubuntuforums.org/member.php?u=731476")

I also created a usb live cd of 10.10 in 10.04 and works perfectly on a laptop (Hp mini 1100). But when I go to my desktop, i just get the "Boot error" above a blinking cursor. 

I've checked the configuration file "syslinux.cfg" for the "ui" string, but is already absent. 

Could you please describe me how did you created you usb live cd?

Kind regards

as I said in post #9,
I first created a live usb using usb creator on the iso in windows xp..
then I booted up ubuntu lucid and re created the usb using create start up disk(NOTE I dint format it AND I kept the Persistance space same as in xp=1GB)
thats it...you have to create the usb two times...I guess this is a bug...someone should file it...

hope it helps...


EDIT: can you list your hardware config? is it similar to mine...might be helpful for filing bug

---

### Post by lopcaf on 2010-10-29
@inso_741

Thanks for your reply!

Desktop: Dell Vostro 200; 3GB RAM; Intel Core2Duo @2.66GHz; Ubuntu 10.04

Laptop: Compaq Mini 110c; N270 Atom @ 1.6GHz; 1GB RAM; HDD 160GB; Ubuntu 10.04

---

### Post by Evilandi666 on 2010-10-31
I have the same Problem,
i got a Ubuntu 10.10 (upgraded von 10.04) and wanted to reinstall it via USB. Created a USB Stick with the USBcreator of Ubuntu, boots on my HP Laptop but not on my Home PC. (says "Boot Error".).

Strange problem..

---

### Post by inso_741 on 2010-11-02
I've filled a Bug [here]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/669778")

those of you having the same problem please subscribe...

---

