---
title: "ubuntu crash! need help!"
date: 2006-04-25
forum: General Help
---

### Post by corey.cn on 2006-04-25
hi, guys!

   my pc installed ubuntu 5.10, few day ago, I used a box of usb,
the box can make me get another 4 usb plugin in my pc's one usb plugin.

    but yesterday&#65292; I shutdowned the linux, the ubuntu tell me something tempfile is busy, so the pc can't be shutdown, then I pushed the button of power, and the pc is shutdown.

     today, when I start the ubuntu, the linux tell me [the /dev/hda1 can't be mounted to /root], and show the console named ash. the ubuntu can't stand.
     
      then, I used the liveCD making the linux stand, and the /dev/hda1 is ok.

      so, I need help to rescue the ubuntu. reinstall the ubuntu is terrible, THANKS a lot.

-----------------------------------
my pc:  thinkpad T20
           ubuntu 5.10

---

### Post by corey.cn on 2006-04-25
I need help!

---

### Post by dg_w on 2006-04-25
Intresting :)
How you partition the install..
Is Ubunto all installed on /dev/hda ? (IDE or the USB disk ?)
Can you boot from the cd into rescue mode. and that finds the ubunto install
Choose the partition and re-install grub ..

Try to reverse what caused the problem... Remove the 4xUSB hub and plug in what you had when you installed Ubuntu..

A bit vague sorrt, but more info will help :)

---

