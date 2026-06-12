---
title: "Sony Ericsson  MBS-100 Bluetooth Speaker on Lubuntu 11.04?"
date: 2011-09-29
forum: General Help
---

### Post by vickoxy on 2011-09-29
Hi,
i bought Sony Ericsson  MBS-100 Bluetooth Speaker for my desktop computer. I paired it with bluetooth manager and blueman-both showing connection, but no sound is coming from device. This audio box should work under ubuntu, but does anyone knows how to make it work in Lubuntu?
Thanks

---

### Post by vickoxy on 2011-10-01
Hi,
i made the box to work, BUT...

> Well, unfortunately, i have no luck with this speaker. If i connect it to ubuntu 11.04 on MacBook Pro speaker is working perfectly.
But with Lubuntu on shuttle xs35gtv2 the sound comes put in waves and interrupted. So i tested live ubuntu 11.04 and have the same issue. So, it could be some hardware issue? I have usb bluetooth dongle. No idea what to do...[http://forum.lxde.org/viewtopic.php?f=8&t=31364](http://forum.lxde.org/viewtopic.php?f=8&t=31364)

I installed the same apps as in macbook, and, as said, i make the box work, but the sound comes out in waves/interrupted. Bluetooth adapter i V2.0.
Anyone has any idea what should i do to get better output?

---

### Post by amjjawad on 2011-10-01
Hope someone with better ideas than ours will jump in to help :)

---

### Post by vickoxy on 2011-10-01
Just  to hear what the problem is, i uploaded one clip:
[http://www.youtube.com/watch?v=jz4ibkOPdMo](http://www.youtube.com/watch?v=jz4ibkOPdMo)

---

### Post by vickoxy on 2011-10-01
Finally - actually, it seems to be hardware problem by my computer. I tested the box on dell mini 9 with Lubuntu and it worked also fine. After that i just put usb bluetooth dongle to another USB - Port - and- voila!!! - works fine!
So it seems that one usb port on my shuttle doesn´t work as it should be.
Thanks a lot amjjawad for help-it seems that missing rfkill was the trigger here. MAybe also pulse bluetooth module-i just installed the same files on lubuntu that i have in Ubuntu, and all should be fine.

---

### Post by vickoxy on 2011-10-01
UPDATE: actually i was happy to early. The box is playing good only at first connection after reboot. As soon as i close app (chrome, vlc) and open another and play something, i have that issue again. Does anyone knows what it should be, or what do i need to make it always working fine as by the first connection?

---

### Post by vickoxy on 2011-10-02
Found help here:
[https://wiki.archlinux.org/index.php/Pu](https://wiki.archlinux.org/index.php/Pu) ... y_problems

1. cp /etc/pulse/default.pa ~/.pulse/default.pa
2. comment out the "load-module module-suspend-on-idle" line in ~/.pulse/default.pa
3. pulseaudio -k && pulseaudio --start


So, finally the box is working as it should. But there is another problem now. If the bt speaker connected wit the computer is, wifi just stops to work-i mean, can not load movies/clips from internet with the box plugged in. 


So, for new problem i started new thread:
[http://ubuntuforums.org/showthread.php?t=1853104](http://ubuntuforums.org/showthread.php?t=1853104)

If anyone can help...

---

