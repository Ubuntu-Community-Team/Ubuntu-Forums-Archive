---
title: "Totally undetected hardware...anything I can do?"
date: 2011-02-12
forum: General Help
---

### Post by whatthefunk on 2011-02-12
Im trying to get my scroll wheel to work on my laptop.  However, its totally undetected.  How can I get my system to recognize it?  Thanks.

---

### Post by DanneStrat on 2011-02-12
> **whatthefunk said:**
> Im trying to get my scroll wheel to work on my laptop.  However, its totally undetected.  How can I get my system to recognize it?  Thanks.

We can try to do a little troubleshooting.

First we need to know what device you

have.

Open a terminal and run this command:

```
lspci
```

Post the output.

---

### Post by whatthefunk on 2011-02-12
Yeah, it doesnt show up in lspci output.  It doesnt make it in lshw or dmesg either.  Its completely undetected by my system.  Its a Sony Jog Dial scroll wheel.

---

### Post by DanneStrat on 2011-02-12
Is it enabled in BIOS?

---

### Post by whatthefunk on 2011-02-12
Hmmm...good question.  I never thought of that one.  It worked when this machine still had WinXP and I never messed around with the BIOS so Id assume so, but you never know.  Rebooting.

---

### Post by whatthefunk on 2011-02-12
There are no hardware configuration options in my BIOS.  So Im assuming it is enabled?

---

### Post by DanneStrat on 2011-02-12
> **whatthefunk said:**
> There are no hardware configuration options in my BIOS.  So Im assuming it is enabled?

What do you get

if you do a lsusb?

---

### Post by whatthefunk on 2011-02-12
Its not there either.

---

### Post by DanneStrat on 2011-02-12
> **whatthefunk said:**
> Its not there either.

We can also check if the jogdial

is presented to the operating system

and find out it's model number.

Do a:

```
sudo dmidecode
```

If you dont find it there

try this instead:

```
sudo dmidecode | more
```

---

### Post by whatthefunk on 2011-02-12
Not there either:)

---

### Post by DanneStrat on 2011-02-12
> **whatthefunk said:**
> Not there either:)

That's strange.:D

The thing with proprietary hardware is that

it can be quite tricky to get working.

There may be something "special" with the

motherboard, which makes it hard for the

operating system to detect the device.

It would be easier if the device came up

detected but "unknown". Then you would have

something to work on.

Keep this thread open for a while.

If I find anything interesting, I will

post it.

What laptop make and model do you have?

---

### Post by whatthefunk on 2011-02-12
Its an older Sony Vaio model PCG-SRX3S/BD
One of my problems is that this model was only distributed in Japan and so all documentation about it is in Japanese...
Thanks for trying to help me out DanneStrat!

---

### Post by DanneStrat on 2011-02-12
> **whatthefunk said:**
> Its an older Sony Vaio model PCG-SRX3S/BD
One of my problems is that this model was only distributed in Japan and so all documentation about it is in Japanese...
Thanks for trying to help me out DanneStrat!

You're welcome!

As I said before, you can return to this thread

in the next couple of days to check for updates.

Have a good day!

---

### Post by whatthefunk on 2011-02-18
So this is weird.  I just had to do a re-installation and in the Xwindow system profiler the Sony Jog Dial shows up.  However, I still cant find it in the out put of any terminal command.  How is that possible?

---

