---
title: "Help with wireless in ubuntu"
date: 2010-05-27
forum: General Help
---

### Post by Ezekiel285 on 2010-05-27
Hi, i am fairly new to ubuntu and i am stuck with getting my wireless card to work. i have seen some similiar posts but nothing has worked for me so far. I just bought an hp dv6 and i dual partitioned it for ubuntu and windows 7. I have transfered the correct driver for my wireless card but am having trouble with the commands. Ill show what ive done so far and hopefully i gave enough info. Any help will be greatly appreciated.
 
I transfered the driver to a temp file called wdrivers and took it out of .tar format. 
I then attempted to remove all other drivers for wireless cards but dont know how to check this. (or look for others?)
 
the guide i used then told me to use this command "make -C /lib/modules/$(uname -r)/build M=`pwd` clean" and then "make -C /lib/modules/$(uname -r)/build M=`pwd`"
 
after this the driver was supposed to work with "sudo modprobe ieee80211_crypt_tkip"
"sudo insmod wl.ko" but i got an unknown symbol error with the last one.
 
hope that makes sense, thanks in advance

---

### Post by spotted zebra on 2010-05-27
try this:

system>administration>hardware drivers

it will take a second to search for new ones, you will want to be connect via LAN. it may or may not give you drivers that you can download and install with that GUI program.

i hope this helps, the way you are going about it seems complicated but i have tried things like that too.

---

### Post by Ezekiel285 on 2010-05-27
Well thats part of my problem too, i have not been able to connect through lan which is why im going about this in such a difficult way. Thanks for the help though, ill try lan again.

---

### Post by spotted zebra on 2010-05-27
let us know how it goes and if you need further assistance.

---

### Post by Ezekiel285 on 2010-05-30
Well i tried lan again and it worked the second time. From there downloading the driver was very easy. I realize how ridiculously overcomplicated what i was trying to do before was, haha. Thanks for the help!

---

