---
title: "Samsung Galaxy 10.1 tab file transfer"
date: 2011-06-18
forum: General Help
---

### Post by clancymf on 2011-06-18
I just purchased the 10.1 tab.  Thinking it would be like my droidx (plug and play) but i was wrong.  It uses MTP protocol and I can't see the 32g of storage i paid so much for.  Im leaving for a trip tomorrow and cant take the time to transfer everything over scp.

Any ideas to i) see the 32gs and ii) transfer data to it.

Regards.

---

### Post by Lennon V C on 2011-06-23
Serious? I was really thinking of picking one of these up. I guess I'll go with the asus Eee Pad Transformer (TF101) or a XOOM.

---

### Post by rochecompaan on 2011-11-01
I got a Samsung Galaxy 10.1 tab yesterday and ran into the same problem on a laptop running Oneiric. I accidentally figured out that you need to install mtp-tools when I plugged it into an older workstation running Hardy and it mounted without problems and I could transfer files to it.

So just do "sudo apt-get install mtp-tools" and you should be on your way.

---

### Post by gandaran on 2011-11-01
> **rochecompaan said:**
> I got a Samsung Galaxy 10.1 tab yesterday and ran into the same problem on a laptop running Oneiric. I accidentally figured out that you need to install mtp-tools when I plugged it into an older workstation running Hardy and it mounted without problems and I could transfer files to it.

So just do "sudo apt-get install mtp-tools" and you should be on your way.
I'm just curious, does MTP work with usb cable only?
how about using FTP server over wireless? that's what I use on my Samsung galaxy phone, no cables.

---

### Post by clancymf on 2011-11-04
> **rochecompaan said:**
> I got a Samsung Galaxy 10.1 tab yesterday and ran into the same problem on a laptop running Oneiric. I accidentally figured out that you need to install mtp-tools when I plugged it into an older workstation running Hardy and it mounted without problems and I could transfer files to it.

So just do "sudo apt-get install mtp-tools" and you should be on your way.

Thanks will give that a try!

---

### Post by clancymf on 2011-11-04
> **gandaran said:**
> I'm just curious, does MTP work with usb cable only?
how about using FTP server over wireless? that's what I use on my Samsung galaxy phone, no cables.

Yes FTP works, although its much slower than the usb connection.  When you have 15+ gig of shows and movies to transfer on it can take alot more time and baby sitting to get it done.

---

### Post by Jboulden on 2011-11-13
Guys,

I am having the same problem, running 10.04.  Installed the MTP-Tools and still no dice.  The computer sees it as an MTP device but does not mount the file system.  I have tried turning on USB debugging but to now avail.  Did the MTP-Tools work for either of you?

---

### Post by TimEnid on 2011-11-13
this is an issue within Honeycomb. i have the same issues with my xoom. no matter what I try, it won't connect properly. I have just decided to transfer vfiles via wifi. I gave up on establishing full USB connection.

---

### Post by josir on 2011-11-14
I didn't get either.

The Android speech as "free software, free everything" does not match with reality.

I prefer Apple: at least they said "I am not free, I am not open buy me if you don't care about it"

<snip>

---

