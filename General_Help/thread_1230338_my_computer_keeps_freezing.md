---
title: "my computer keeps freezing"
date: 2009-08-03
forum: General Help
---

### Post by rhythmiccycle on 2009-08-03
all of a sudden my computer keeps freezing up,

i reinstalled ubuntu hopeing to fix the problem but its still freezing.

what should I do?

---

### Post by wojox on 2009-08-03
Wrap a blanket around it. :D

No really when does it freeze up? Are you running any apps at the time? Does it just happen out of blue? Laptop or Desktop?

---

### Post by rhythmiccycle on 2009-08-03
it seems to be freezing out of no where.

last night it froze. the only program running was firefox, and it had my gmail page on it.

then i reinstalled ubuntu, and it froze while it was updating.

then i wouldn't start up (i think because of the freeze during the update)

i'm reinstalling ubuntu now.

every thing was working fine before, this problem just started yesterday.

---

### Post by ibuclaw on 2009-08-03
Run in a terminal:
```
dmesg > dmesg.txt
```
And attach the resultant file to your next post.


In the meantime, if you system freezes, run the following to safely reboot:

Hold down: **Alt+PrintScreen**
and press one after the other (count about 3 seconds between each key): **R E I S U B**

Regards
Iain

---

### Post by arqbrulo on 2009-08-03
Ever since I fixed my "freezes", I've been recommending this:

If REISUB does not work, maybe you have a few lights blinking, etc. Then it's a kernel panic. I was having those every time I would use my computer. It turns out I had a bad sector on my disk. I ran "fsck -c /dev/sda" and I have not had the problem since.

---

### Post by rhythmiccycle on 2009-08-03
i just reinstalled ubuntu, and then did

dmesg > dmesg.txt

it is attached

(i had to break it into 2 files, because it was too big for the forum to let me post it)

also i tried

```
sudo fsck -c /dev/sda
```

and i get the message > fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?


do i need to be booted off of the live CD to run that code?

---

### Post by ibuclaw on 2009-08-03
> **rhythmiccycle said:**
> i just reinstalled ubuntu, and then did

dmesg > dmesg.txt

it is attached

(i had to break it into 2 files, because it was too big for the forum to let me post it)

also i tried

```
sudo fsck -c /dev/sda
```

and i get the message 

do i need to be booted off of the live CD to run that code?

Do you connect to the internet via ethernet?

---

### Post by arqbrulo on 2009-08-03
> **rhythmiccycle said:**
> 
do i need to be booted off of the live CD to run that code?

Not really, either boot off a livecd or boot in recovery mode and go into command prompt.

---

### Post by rhythmiccycle on 2009-08-03
> Do you connect to the internet via ethernet?

I have (Coaxial) cable Internet, going into a modem,
*an Ethernet cable connecting the (Coaxial) cable modem to a netgear router. 
*then another Ethernet cable connecting the router to the computer.
*(the router is also sending out a wireless signal for my laptop)

---

### Post by HavocXphere on 2009-08-03
> **rhythmiccycle said:**
> what should I do?
Run memtest for a couple of hours.

On a slightly offtopic note: I had a total freeze yesterday.:frown: First time that happened on Ubuntu. Possible related to new .14 kernel.

---

### Post by rhythmiccycle on 2009-08-03
> **arqbrulo said:**
> Not really, either boot off a livecd or boot in recovery mode and go into command prompt.

i tried running while booted off the liveCD:
```

sudo fsck -c /dev/sda

```

but i still get the message
> 
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?



i also tried booting in recovery mode. i saw the option "fsck" and hit enter on that, after it did its thing it said something like: "2% noncontinuous [something]..." 
the code"fsck /dev/sda" was used, the "-c" was left out

i didn't see how to go into command prompt, so i could add the -c to the fsck.

---

### Post by arqbrulo on 2009-08-03
Ok, then. First of all, sorry for giving you "partial" information. I'm telling you what I did from what I can remember, and I might forget a few details. Second, if you only have one partition, or if you are trying to check the root partition, then you DO need to run the command from a LiveCD environment. If you think the damage is somewhere in your "/home" partition, then run "fsck -c /dev/sdaX". Third, in Jaunty, when you boot into recovery mode, it gives you some sort of menu, in that menu there's an option to open a shell prompt, or something with the word "shell". That's where you would run the command from.

Now, I don't really know why the LiveCD is giving you that error. Maybe you need to specify a partition to the command? (eg "fsck -c /dev/sdaX")

Once again, my computer was having problems similar to yours, and this worked for me, it might not work for you. Your problem could be something completely different.

---

