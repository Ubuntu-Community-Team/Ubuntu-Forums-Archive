---
title: "MP3 Player not connecting"
date: 2010-01-23
forum: General Help
---

### Post by Bini_1 on 2010-01-23
I have a new MP3 player that works fine if I connect it to my Windoze laptop, but when I connect it to my Ubuntu PC I cannot see it.

If I do lsusb, it doesn't appear in the list of devices

I am not using an extension cable, I have tried unplugging all the other USB devices, but still nothing

Any suggestions

---

### Post by jamesisin on 2010-01-23
Which make and model of PMP?

---

### Post by Bini_1 on 2010-01-23
It's just a cheap generic one

---

### Post by jamesisin on 2010-01-23
Is that Generic by Cheap or Cheap by Generic?

Really though knowing the make and model will be helpful.  Probably they don't make their own anyway.

---

### Post by Bini_1 on 2010-01-23
It has no manufacturers name or model name on it or the packaging

---

### Post by Wandering Ronin on 2010-01-23
Does it have any distinguishing features such as height, weight, eye color, tattoos or birthmarks? 

Seriously, though, is there any indication of what it is when you plug it into your Windows machine? Some little something that suggests Sansa or Fred's MP3?

---

### Post by Bini_1 on 2010-01-24
It is the same as this item on ebay : 250565921614

---

### Post by jamesisin on 2010-01-24
Wow.  So it's probably something like this:

[http://technologizer.com/2008/12/22/ifrauds-the-fakest-ipods-ever/](http://technologizer.com/2008/12/22/ifrauds-the-fakest-ipods-ever/)

Could be difficult to sort out who made it and what OS or firmware it's running.  I know some of them run Java, but...

You might try manually mounting the device.  You'll have to dig through /dev to figure out which device is the correct one.

Maybe someone else has other suggestions?

---

