---
title: "how to mount micro sd card"
date: 2009-09-05
forum: General Help
---

### Post by blur xc on 2009-09-05
I've got a multi card reader in my pc, and normally when I insert a card I'll see it in my places in nautilus (and an icon on my dekstop), and then I can double click it to mount it.  But- I'm not seeing anything right now.  I'm somewhat versed on mounting, and have done a bit of that w/ partitions and an external drive (edited the fstab also), but I'm clueless where to start on this one.

I can checked the /dev folder, and there's a ton labled usb something or other, and I have no idea what "port" the micro sd card slot is.

Thanks,
BM

---

### Post by woedend on 2009-09-05
Are you sure that your card reader is even working with Ubuntu?  It should be automounted.  As for me, i've never been a big fan of card readers and find them somewhat redundant.  I use a USB dongle with card reading capabilities...that was I can load it on machines without card readers or with.  Put card into dongle, plug dongle into PC...automounted.  Here is an example product(the one I use)
[http://www.google.com/products/catalog?q=mobilemate+sd&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&ie=UTF-8&cid=13374329539839407456&ei=f-2iSqapHYaHtgfj5ZX7Dw&sa=X&oi=product_catalog_result&ct=result&resnum=2#ps-sellers](http://www.google.com/products/catalog?q=mobilemate+sd&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&ie=UTF-8&cid=13374329539839407456&ei=f-2iSqapHYaHtgfj5ZX7Dw&sa=X&oi=product_catalog_result&ct=result&resnum=2#ps-sellers)

I know that doesn't exactly fix your problem, but just offering a suggestion.
As a side note...if your card is unformatted, it will not be automounted.

---

### Post by blur xc on 2009-09-05
> **woedend said:**
> Are you sure that your card reader is even working with Ubuntu?  It should be automounted.  As for me, i've never been a big fan of card readers and find them somewhat redundant.  I use a USB dongle with card reading capabilities...that was I can load it on machines without card readers or with.  Put card into dongle, plug dongle into PC...automounted.  Here is an example product(the one I use)
[http://www.google.com/products/catalog?q=mobilemate+sd&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&ie=UTF-8&cid=13374329539839407456&ei=f-2iSqapHYaHtgfj5ZX7Dw&sa=X&oi=product_catalog_result&ct=result&resnum=2#ps-sellers](http://www.google.com/products/catalog?q=mobilemate+sd&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&ie=UTF-8&cid=13374329539839407456&ei=f-2iSqapHYaHtgfj5ZX7Dw&sa=X&oi=product_catalog_result&ct=result&resnum=2#ps-sellers)

I know that doesn't exactly fix your problem, but just offering a suggestion.
As a side note...if your card is unformatted, it will not be automounted.

Isn't a card reader pretty much the same thing, except I have mine mounted inside the case?  Acutally, the one I have can go both ways, external or internal.  I'm fed up with external ones.  It's a pita, and most don't read udma cf cards, which makes them a deal breaker.  And yes, I've used it plenty of times in Ubuntu and it works awesome.  I couldn't be happier.

Here's the one I bought- [http://www.newegg.com/Product/Product.aspx?Item=N82E16820176015](http://www.newegg.com/Product/Product.aspx?Item=N82E16820176015)

BM

---

### Post by JC Cheloven on 2009-09-05
Let's see if ubuntu recognizes the card reader. Could you please post the output of

```
grep -i 'card' /var/log/dmesg
```

---

### Post by blur xc on 2009-09-05
> **JC Cheloven said:**
> Let's see if ubuntu recognizes the card reader. Could you please post the output of

```
grep -i 'card' /var/log/dmesg
```

ok-

```
grep: /var/log/dmesg: Permission denied
```
Just kidding- added the requisite sudo

```
[    0.884680] isapnp: Scanning for PnP cards...
[    6.980390] EISA: Detected 0 cards.
```This card has worked in the past.  It's a 2gb micro sd card that normally resides in my cell phone.  About a month ago, I plugged it in and transferred all the pictures and music off of it to this computer.  I wonder if I can reformat it in my phone or something.  Could this be caused by a un-clean removal?

thanks,
BM

ps- the blue light on the card reader did blink a few times when I first plugged it in.  Don't know exactly what that means, but at the very least it realized something was plugged in.

---

### Post by woedend on 2009-09-05
could be...but in theory, if it works in your phone it *should* work in your pc.

---

### Post by kaligus on 2009-09-05
I just searched for my problem and found this so rather than start a new thread for the exact same-ish problem I will add my info here.

I am having similar issues with a Kodak multi card reader that has worked well under everything until Jaunty where some cards will randomly automount and others will not.  

My wife thinks she also had troubles mounting cards under Intrepid but I do not recall any.

I thought at first maybe size but the only one that consistently doesn't automount is a 4GB sd card full of windows portable stuff.

All other cards ranging from 8MB "smart media" to 4GB "SD" randomly automount or not depending on the mood of the gods.  

The cards tried are "smartmedia", "CF", "SD", "micro-sd in adapter" and the long sony I think are called "MS-memory stick" which a friends mp3 player uses.

If I run virtualbox and pass through the USB for the Kodak reader it "always" works as expected.

If I use a specific USB-SD reader (targus and walmart cheapie are the two I have) the automounting is less random and more auto but there is still a time once in a while that the card will not mount.

I have just swapped cards, and unplugged, counted to twenty, reinserted the same card and the automount is truely random.

I can get at most 10 in a row of the same card automounting following itself only.  At most 3 times with other cards between.

When automounted the Kodak takes the following devices:
CF card /dev/sde
MS card /dev/sdf
SD card /dev/sdg
SM card /dev/sdh
USB SD only reader /dev/sdi
virtualbox automatically sets up devices e: f: g: h: for the kodak and e: or i: for the USB SD only readers depending on if the kodak is connected or not.

When the automount does NOT work these devices give the error
root@bigwill:~# mount /dev/sdg /media/portable
mount: special device /dev/sdg does not exist

I suspect there is something in the event system that sets up the special devices that is not doing what is expected but that is only a slightly educated guess LOL

---

### Post by blur xc on 2009-09-06
Crazy thing mounted today.  I didn't even do anything.  :confused:

Thanks anyway,
bm

---

