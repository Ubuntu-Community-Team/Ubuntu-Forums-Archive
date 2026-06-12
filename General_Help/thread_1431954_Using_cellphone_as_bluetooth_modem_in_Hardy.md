---
title: "Using cellphone as bluetooth modem in Hardy?"
date: 2010-03-17
forum: General Help
---

### Post by t0p on 2010-03-17
I recently got myself a bluetooth dongle.  I frequently use my Sony Ericsson K800i mobile phone as a modem to connect my computers to the internet.  I've had to use a USB datacable to link phone to computer, so I'm pretty stoked at the idea of using a bluetooth connection instead.

I used [this tutorial]("http://www.spiration.co.uk/post/1307/Ubuntu%20Linux%20-%20Bluetooth%20and%20GPRS%20dialup%20connection") to set up the modem connection.  It's a bit aged: it was written in the days of 6.10, and goes on about *bluez-utils*; but it wasn't hard to update it, for instance replacing the command

```
sudo /etc/init.d/bluez-utils restart
```

with

```
sudo /etc/init.d/bluetooth restart
```

and there's now a little graphic interface to pair devices and such, whereas when the tutorial was written you had to use command-line to pair and authenticate.   Also, I use Gnome-PPP to start the internet connection rather than the *pon*and *poff* commands suggested in the tutorial.

Anyway, I can connect to the phone/modem simply enough now with my EeePC running Jaunty.  But when I put the same dongle in my Hardy-running desktop machine, I cannot establish a link.  This really puzzles me: the same bluetooth device is being used in both cases, and I'm following the tutorial in both cases so I'm doing the same in both cases.  I can do other stuff with the dongle and the Hardy box: for instance I can transfer files from one to the other.  It's just the dial-up internet function that won't work.

I realise the next LTS version (Lucid) is coming out soon; and I'm pretty confident the bluetooth modem connection will work okay with Lucid.  But in the meantime, I really would like to use the bluetooth connection now.  Sometimes my phone can get a 3G signal only if it's sitting onmy window sill, and the datacable isn't long enough to do that.  So, if anyone can point me in the right direction for info on how to use a phone as bluetooth modem with Hardy, I'll be very grateful.

Cheers!  t0p.

---

### Post by t0p on 2010-03-19
bumpity-bump.

Surely there's someone here who uses/has used a cellphone as bluetooth modem with Hardy?  Surely someone knows what's wrong with my set=up?

Hellllp!!

---

### Post by t0p on 2010-03-22
Things that go bump in the night include this thread.  but it's *me* who's making it bump, and I really hoped someone else could help.

Anyhoo, this is the last time I'm going to bump this.  I *know* someone here has used a cellphone as bluetooth modem with 8.04.  So *pleeeeze* reveal the arcane knowledge I crave!

To recap: I can use my Sony Ericsson K800i as a bluetooth modem with 9.04.  It also does file transfers and even the phone's built-in "remote control" utility works after a fashion.  But with 8.04: file transfer over bluetooth works, but I can't use the phone as a bluetooth modem (I *can* use the phone as modem with 8.04 if I use a USB datacable to connect; but not with bluetooth).  Remote control also won't work with 8.04, but that isn't a real problem for me.

So come on: help me out!  You know you want to...

---

### Post by cogier on 2010-03-22
I had a Sonny Ericsson and tried to get it to work with Hardy with no luck. If you can upgrade to 9.10 the tools are vastly better for doing this.

---

### Post by t0p on 2010-04-07
Well I guess I may as well mark this as 'SOLVED' even though it isn't.  I'll have to wait til I upgrade my desktop to Lucid then try again.  Sigh.

---

