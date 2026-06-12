---
title: "copying from one usb external hd to another - how to speed up?"
date: 2010-08-25
forum: General Help
---

### Post by keithpeter on 2010-08-25
Hello All

I'm copying about 190Gb of files from a 250Gb external usb hard drive to a 1Tb external drive, rationalising the backups. Many files, up in the hundreds of thousands.

Foolishly perhaps, I did a drag and drop between two nautilus windows on Ubuntu, its taking hours, and its also taking most of the memory in the desktop PC and slowing the interface down badly.

Is this normal? If so, would mv at the command line be quicker? Or wget?

When I say 'quicker' I'd settle for a usable desktop while the transfer was happening. It started off usable but Gnome became progressively more sluggish as the transfer proceeded. Any way of 'rationing' the resources given to the file transfer?

I'm posting this from the laptop. I have another couple of smaller hard drives to transfer.

Cheers

---

### Post by sikander3786 on 2010-08-25
If there are too many smaller files, it is normally a slow file transfer as compared to 1 big sized file, however it shouldn't slow down the desktop. How much RAM do you have?

---

### Post by Rubi1200 on 2010-08-25
System > Administration > System Monitor > find the relevant process and right-click then Change Priority

---

### Post by keithpeter on 2010-08-25
Hello Both

2GB and 1.8 is currently in use, I have system monitor running with the 'resources' tab visible

Its taking about 10 minutes to change windows so I'll just leave it to finish right now!

Is there a way of assigning file transfers a lower priority before you start one?

Would command line (e.g. mv) be quicker / less clobbering?

Thanks

---

### Post by TyLLy_4 on 2010-08-25
this might sound dumb (and it probably is) 

but, make sure you are plunging both devices on usb 2.0 ports (most computers iv seen have one set of 1.0 and another set of 2.0)

also. consider doing this overnight?

---

### Post by Rubi1200 on 2010-08-25
Look at the manpages for mv, but I think that would be better. Right now you are in the middle and certainly don't want to stop things!

---

### Post by keithpeter on 2010-08-25
Hello TyLLy_4

Dumb is a possibility in this case, the 1Tb drive is in one of the two rear USB ports, the old 250Gb drive I plugged into one of the two front panel USB ports... 

But then if transferring at USB 1.1 rate, why is it clogging the machine so heavily? It should just trickle.

Looks like it WILL be overnight...

Cheers

---

### Post by keithpeter on 2010-08-26
Hello All

I tried the cp command from a terminal and it copied the files a little bit quicker (but we are talking hours here) and the desktop remained responsive throughout, RAM use being a hundred or so Mb more than quiescent.

I'd love to know what it is about Nautilus that makes large file copying so inefficient.

---

