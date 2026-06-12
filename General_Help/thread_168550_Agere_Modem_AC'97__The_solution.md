---
title: "Agere Modem AC'97 : The solution"
date: 2006-04-30
forum: General Help
---

### Post by Runspect on 2006-04-30
It's incredible (for me), but true, works. I've followed the instructions of:

[http://linmodems.technion.ac.il/travelmate800.ubuntu.slmodem.html](http://linmodems.technion.ac.il/travelmate800.ubuntu.slmodem.html)

And now the modem is working fine on my Compaq Presario v4000 under Kubuntu 5.10. The difficulty level is very high, but it is worth trying.

---

### Post by towsonu2003 on 2006-04-30
just some notes for anyone coming accross this:
modemdata.txt key words:
> Smartlink software in ALSA mode may support this modem 
 The Subsystem PCI id does not itself identify the modem Codec.

  Driver snd-intel8x0m  may enable codec acquisition

hence, if you decide to try a liveCD and want dial up connection from it, try the precompiled package at [http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD-2.9.9e-pre1-alsa.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD-2.9.9e-pre1-alsa.tar.gz)

untar and cd to its directory (SLMODEMD), change it to executable (chmod +x slmodemd), and use it with
./slmodemd -a -c USA hw:0
-a means alsa support
-c means country
instead of hw:0, it might have been hw:1 or modem:0 or modem:1
---root privileges needed to run

I find it quite useful every time I try a liveCD for a couple of hours, without having to deal with each distro's own "way of slmodeming" :)

Thanks for letting us know of your success :)

---

