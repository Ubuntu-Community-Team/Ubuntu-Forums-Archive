---
title: "Freezing at startup"
date: 2011-04-22
forum: General Help
---

### Post by yipyip123 on 2011-04-22
I ran the update manager for ubuntu for the first time in a couple weeks. A restart was required. Upon restarting, ubuntu was asking for my password (to probably continue the update), which it usually doesn't. Nothing was "clickable" or typeable. It just appeared to be frozen, except it would search for wireless still.

What is my problem and how do I fix it? I am a bit of a noob.

edit: unrelated, but my mouse only works in ubuntu, but not windows. Any way  to fix this? It's a logitech mouse...

---

### Post by yipyip123 on 2011-04-22
Can someone please help with this problem? I have no idea what to do.

When I start ubuntu, I see the "keyring" window, asking me for my password, but I can't type into it because I can't click anything.

HELP!

If there is no solution. Is it possible to access my ubuntu files from windows??? I'm desperate...

---

### Post by Rubi1200 on 2011-04-23
Hi,
what version of Ubuntu are you using and is this a Wubi install?

what graphics card do you have installed?

have you tried booting an older kernel or recovery mode?

---

### Post by yipyip123 on 2011-04-23
> **Rubi1200 said:**
> Hi,
what version of Ubuntu are you using and is this a Wubi install?

what graphics card do you have installed?

have you tried booting an older kernel or recovery mode?

I believe I'm using 2.6.32-31 and/or 10.04.2. Not sure what those numbers mean.

I've never heard of Wubi, so I assume not.

My graphics card is nvidia geforce gt12014

I've tried booting multiple older kernels (versions?) and also recovery mode. All of them lead to my desktop, with a window asking me to unlock my keyring, but everything is just unclickable or untypeable.

i've tried "sudo service gdm restart" but that did nothing...

any other ideas?

---

### Post by Rubi1200 on 2011-04-23
When the computer starts and you see the entry for Ubuntu highlighted press "e" to edit.

Use the arrow keys and navigate to the line that ends with quiet splash.

Add nomodeset after it so it looks like this:

> quiet splash nomodeset

Then, "Ctrl" + "x" to boot.

Let me know if this helps.

The other thing to look at is whether compiz (desktop effects) are enabled and then turn it off.

---

### Post by KegHead on 2011-04-23
Hi!

Try:

system..preferences....start up applications..check all boxes.

KegHead

---

