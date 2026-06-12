---
title: "Problems with Samsung n150"
date: 2010-06-05
forum: General Help
---

### Post by Thomas Humphrey on 2010-06-05
Just installed on my netbook the latest version of ubuntu (10.04). Have seen a few issues with other users however they have seemed to be able to make fixes.
My problems are:
- Screen half brightness no change (does anyone have a fix yet?)
- Wifi not working (tried updating kernels, says they're the latest)
- Multi touch not able to be enabled, (again have seen a fix but for some reason won't work)
I am a bit of a newbie and only used an older build of ubuntu in VM's before. 
If anyone could lend a hand it would be most appreciated.

---

### Post by postadelmaga on 2010-06-13
ok try that ppa:
[https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

It has all the stuff you need to make n150 work !!!

just add " ppa:voria/ppa " to software source 
and install " samsung-tools "
then you'll have a new gnome-applets ...

---

### Post by theroquentin on 2010-06-15
Hello

I've recently bought a Samsung n150 netbook.  It has Windows 7 Starter on it.
I've never used ubuntu but am keen to try.  I don't want to wipe Windows 7 Starter of my N150 as this voids the warranty and I will still use it sometimes anyway

I bought a 16gb USB stick to use to boot ubuntu on the netbook.  The USB stick works it boots UBUNTU netbook 10.04, but the wifi doesn't work.

The reply above doesn't make any sense to me.  I've done lots of google searches and now this is a problem with Samsung 150s, but I don't understand the solutions.

I'm completely new to Ubuntu, is there a more step by step guide I could follow to get wifi working on my samsung n150 (booted from usb stick)?

Thanks

Neale

---

### Post by postadelmaga on 2010-08-20
wellcome to ubuntu comunity :),
consider all samsung n150's hardware work out of the box with ubuntu ...
The above discussion is all about the fn key ... for disable wifi, more less brightness ecc...

Maybe the wifi doens't work only cause it is disabled and the fn key doens't work without [PPA Voria]("https://launchpad.net/~voria/+archive/ppa") ( ppa are extra repository for ubuntu )

How u can go on: 

**One quickway is to enable wifi in the bios by default.**

**Or u can add Voria's repository on ubuntu and enable fn key: **

1.open a terminal and digit

```
sudo add-apt-repository ppa:voria/ppa
```

now the repository is been added to your list ... 

2. update the list of package :

```
sudo apt-get update && sudo apt-get upgrade
```

3. install the package you need :

```
sudo apt-get install samsung-tools samsung-backlight easy-slow-down-manager
```

now reboot and the u'll have the fn key working ...

you also have **samsung-tools**: an applet for gnome ( right click on the desktop bar ... "add applets" ) look for it and add.

**samsung-tools** let u controll wifi, bluetooth, fan speed and other tune option by gnome


-- you can also ask for support on: [Voria Forum]("http://www.voria.org/forum/viewforum.php?f=3") or just to say thank u to Voria 

I hope that help u.

Sorry my english is not so good as i want :)

---

### Post by fanism on 2010-10-17
hi, 

thanks for the tips here, however, when i was doing the code 3,

sudo apt-get install samsung-tools samsung-backlight easy-slow-down-manager
[FONT=monospace]
the system told me it failed, the "samsung-tools" not found.  Do you know how to fix this?  thanks

- vanessa
[/FONT]

---

### Post by processor on 2010-10-20
Did you sort this out yet?
Please tell me if you did.

P.

---

### Post by gokulsurendiran on 2010-10-23
Hi,
Bought this samsung n150 with win 7, installed ubuntu 10.04 and I too had the same problems.
I also use Ubuntu(dual boot with win XP) in my laptop Lenovo B450, but never opened this "terminal".

Just came across this posting and steps described by "postadelmaga", copy & pate in my terminal, it worked!!!!

Ubuntu is great, but i only miss MS office, didn't find open office as friendly as MS office.

One more qn - is ubuntu 10.10 is better than 10.04; does 10.10 come with all this upgrade?

Thanks to postadelmaga & Voria

Gokul

---

### Post by Bensachs on 2011-03-02
Hi there!

The solution posted by postadelmaga worked fine for me until recently.
I don't know whether it's got to do with Ubuntu going from 10.04 to 10.10,
but the Fn-keys for regulating the backlight don't work any more, which pretty much sucks.
All the rest of them are doing fine, but those aren't working.

---

### Post by ucob012z on 2011-07-17
To fanism & Bensachs

just try it



sudo add-apt-repository ppa:voria/ppa


sudo apt-get update && sudo apt-get upgrade


sudo apt-get install samsung-tools samsung-backlight

insyaallah will be okay.......

---

