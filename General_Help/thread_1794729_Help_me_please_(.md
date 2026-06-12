---
title: "Help me please :("
date: 2011-07-01
forum: General Help
---

### Post by BradRocheee on 2011-07-01
I installed ubuntu 11.04 on my dell inspiron mini 10. I replaced windows 7 starter but i want to change back as it keeps dropping my wifi connection. Can someone please help to get windows 7 back?

---

### Post by collisionystm on 2011-07-01
> **BradRocheee said:**
> I installed ubuntu 11.04 on my dell inspiron mini 10. I replaced windows 7 starter but i want to change back as it keeps dropping my wifi connection. Can someone please help to get windows 7 back?

Do you have a Windows 7 Cd that came with your computer? 

If not... You probably wiped your whole drive and lost it.

You will need to call Dell and get a replacement CD or let us help troubleshoot your wireless issue.

---

### Post by BradRocheee on 2011-07-01
Its a netbook so i cant put a cd in. If the wifi problem can be fixed ill keep ubuntu. I have to disable wireless then connect it every time i turn on my netbook.

---

### Post by mikejonesey on 2011-07-01
lol oops,

use lspci to dump us the data of your wirless card (lspci -vvv) and lsmod to give us a dump of you current kernel modules (lsmod | sort), although i must say ubunutu is pretty good at matching drivers to use...

still i had to download latest source for my wireless card...

when you say the starter do you mean you get a grub boot loader still or you've fully replaced windows?

---

### Post by BradRocheee on 2011-07-01
no starter was the edition of windows 7 that was on my netbook.(I think this is because its smaller than a laptop and cannot run the full windows 7 properly). I have also deleted windows 7 aswell. Is there anyway of getting windows 7 back the same way as i got ubuntu?

---

### Post by mikejonesey on 2011-07-01
unfortunatley for you unless you created;

1. a system image
2. a recovery disc

or

1. laptop came with a recover disk

(when i say disk or image - usb as you have no cd drive)

then you'd have to pay windows about £50 for new oem discs... (maybee more as it's not cd/dvd...), which is why alot of people hate windows... (this includes even if you have an oem licence key on the bottom of your netbook)... makes you fume huh...

do the dumps ur wirless can and will work in linux...

---

### Post by mikejonesey on 2011-07-01
```

lspci -vvv
lsmod | sort

```

---

### Post by BradRocheee on 2011-07-01
Where do i type them into?

---

### Post by whatthefunk on 2011-07-01
Is there a Windows sticker on the bottom of your laptop?  Isnt it possible to download Windows with the code on this sticker?

---

### Post by kanishkdudeja on 2011-07-01
> **BradRocheee said:**
> Where do i type them into?

Into the terminal.

Click on Applications, Click on Accessories and then open the terminal..

and then run those commands.

---

### Post by Swagman on 2011-07-01
press ctrl + alt + t to get a terminal

---

### Post by BradRocheee on 2011-07-01
Is it possible to create a system image from another computer and use it on mine?

---

### Post by adit on 2011-07-01
Get Windows 7 dvd and do a fresh installation.  No other ways.
In future before installing ubuntu divide your hard disk into atleast 2 partitions. One for windows and another for ubuntu

---

### Post by goldshirt9 on 2011-07-01
> **BradRocheee said:**
> no starter was the edition of windows 7 that was on my netbook.(I think this is because its smaller than a laptop and cannot run the full windows 7 properly). I have also deleted windows 7 aswell. Is there anyway of getting windows 7 back the same way as i got ubuntu?
you can download starter from a torrent .they are available.;)
i'm unsure if you could use the s/number from the sticker on the base of the netbook ???

something called 
dazloader ;) may help  ( google it)

install instructions via usb as per ubuntu.
ensure bios is set to install from usb as first option.

---

### Post by lisati on 2011-07-01
> **goldshirt9 said:**
> you can download starter from a torrent .they are available.;)

Be wary of illegal copies (which we don't support here), they have been known to contain malware.

---

### Post by goldshirt9 on 2011-07-01
i wouldn't even recommend illegal copies.:D
been there , seen it, done it,  OUCH.:(
all depends on where are they are from.

you could contact dell for a re-installation option of the software.

dont mention what you tried to do and see what they say

---

### Post by mikejonesey on 2011-07-02
> **BradRocheee said:**
> Is it possible to create a system image from another computer and use it on mine?

nope lappys ship with oem versions which are good to go for the machine they are paired with only; if u get a download version (illegal version) you are open to all sorts of security risks ie, keyloggers built in...

if you want windows back you'll need to pay the retailer to get the oem version back...

---

