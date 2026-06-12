---
title: "Headjack not supported =["
date: 2010-05-22
forum: General Help
---

### Post by Simon_WM on 2010-05-22
Hi Guys,

My Laptop (Studio 1558) got 10.4 LTS
i've got a problem with the headphone jack... When i plug in to my desktop speakers noting comes out... 

But when am running windows 7 OEM they work fine...
any ideas

---

### Post by monsterzero on 2010-05-30
I have a Dell Studio 17 and had the same problem with Karmic, which I was able to fix by adding 

-options snd-hda-intel model=dell-m6 

 to the end of the alsa-base.conf file.  Now that I have upgraded to Lynx, my headphone jacks are dead again, and this fix isn't working for me.

  The computer seems to know that the jacks are there, because it cuts power to the built-in speakers when I plug in headphones, but no signal is sent to the phones.  Anyone? 

Edited To Add:  [FIXED] I had a hyphen in front of the options line.  Instead try adding 

options snd-hda-intel model=dell-m6

to the end of /etc/modprobe.d/alsa-base.conf

It worked for me.

---

### Post by drpepper on 2010-07-29
I can confirm adding the line to alsa-base.conf in 10.04 with the Dell Studio 1749 enables the headphones.

Thanks guys :)

Nick.

---

