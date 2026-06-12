---
title: "Ubuntu will not boot"
date: 2011-07-06
forum: General Help
---

### Post by cha0s619 on 2011-07-06
Hi

My pc went kaput a while ago and I've been using my friends laptop for the mean time. The HDD is having issues so I've been running ubuntu 10.04 on a live 8gb flash with persistence. I got real comfortable with this and saved important data on the live usb.

Earlier today the pc did not shutdown correctly. When I restarted, ubuntu started booting and even showed the 5 moving dot loading screen, then it suddenly stopped and displayed the following:

> 
[ 5.352305] xor: automatically using best checksumming function: pIII_sse
[ 5.372009] pIII_sse  : 7319.000 MB/sec
[ 5.454616] device-mapper : dm-raid45 initialized v0.2594b
[ 5.452011] xor: using function: pIII_sse (7322.000 MB/sec)


I know the issue is not with the PC because I can run other ubuntu live usb with no problem. I only have an issue with this one. I found that I was able to mount the casper-rw from the live usb on another machine so my data is ok.

Any idea how to fix this?

Thank you

---

### Post by cha0s619 on 2011-07-11
bump. anything? please I have bitcoins stuck on this installation.

---

### Post by Groggster on 2011-07-11
Well, if it is just the data you are interested in, you might want to try to run another live-cd/USB/whatever, then mount your "defective" USB-Drive and then move the files you are interested in. Or perhaps you can chroot into your newly mounted OS? Anyone?

---

### Post by cha0s619 on 2011-07-13
I tried mounting casper-rw to another ubuntu machine and it worked but the file I want (wallet.dat for bitcoins) is in an encrypted folder and I don't have the key. I guess that means the only way of getting it would be to somehow fix the OS and boot it.

---

### Post by Groggster on 2011-07-17
Now i am not sure about this, but it might be worth trying. Boot your system with a medium that you know work. Then mount the flash drive, to for instance /mnt. After that you should just have to run the command: chroot /mnt. This should grant you access to your files.

[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)

---

