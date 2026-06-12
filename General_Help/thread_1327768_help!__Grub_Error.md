---
title: "help!  Grub Error"
date: 2009-11-15
forum: General Help
---

### Post by ebgbnet on 2009-11-15
howdty dowdy, a newb in these parts, and have got my knickers in a major twist!

a relative newcomer to proper linux (been a mac user for way too long) and have a machine I've kinda hurt (a bit)

right then, the machine belongs to a friend of mine is a dell optiplex GX620.  the drive has fedora on it (version4!!) and some rather expensive software (OLEX) installed on it.  

I shoved a USB memeory stick in and booted it into Ubuntu (latest version with all updates)

everything was fine and dandy for a while, I could pull the usb and it would fire back up to installed fedora/OLEX no problem.

now though, if I try to fire it up from just the internal fedora olex combo I get a Grub error: no such disk

if I shove the USB thing back in, the grub menu comes up and allows me to choose either ubuntu or the internal fedora/olex

problem is, it won't start from the internal if I haven't got the USB stick plugged in (and this machine runs a complex navigation system on a big boat which is due back at sea in 48 hours!)

clearly the internal fedora system is fine and it works perfectly as long as the USB thing is plugged in when grub tries to load.  but I need to get it restored so it will just turn on and work without it plugged in



any suggestions for a complete numpty !

Ta muchly

mark

---

### Post by nathan726 on 2009-11-15
Hi Mark,

Boot up Fedora using the usb
Remove the usb drive
Open a terminal (Applications > Accessories > Terminal) and type:
```
sudo grub
find /boot/grub/stage1
```And use the returned value in place of (hdX,Y):
```

root (hdX,Y)
setup (hdX)
quit

```Reboot without the usb drive and hopefully it works.

---

### Post by ranch hand on 2009-11-15
I hope you have  a CDrom on that thing.  You need a LiveCD.

You need one that uses grub-legacy so Ubuntu 9.10 will not do.

I am assuming that you are using  Ubuntu 9.04

Pull your device out when you have the CD downloaded and burned.

Boot to the CD.

Pull up the terminal.
```

sudo grub

```
This will bring up a prompt like this;
> 
grub>

The following command go in on the grub prompts in this order;
```

find /boot/grub/stage1

root (hdx,y)

setup (hdx)

quit

```
Find will list what it finds for grub in this manner - (hdx,y) - where x is the drive and y is the partition.
Counting starts with 0.  If grub is on the first drive and first partition it will read - (hd0,0).

Root tells grub were to look for the one you want is (the find list can be quite long on some machines with many OS')

Setup tells grub where to stick it.  You should be able to tell if it worked.

Quit tells grub to quit.

You should be able to boot now so just reboot.

---

