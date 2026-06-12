---
title: "Grub rescue error required...help"
date: 2012-01-16
forum: General Help
---

### Post by sofasurfer on 2012-01-16
I disconnected my hard drives so that I could test some extra hard drives that I acquired. Afterwards, when I put everything back together, when I boot up I get a command line screen that says "grub restore". But if I boot up and go to the boot menu and choose my drive it boots fine.

I have hooked up other drives many times and never had this problem. Why did it happen this this? What do I need to do to fix it?

I assume I nned to go to a terminal with my live cd and enter a command but I am unfamiliar with this process. Can you help me?

EDIT: I also notice that my boot drive shows on the menu as #2 and my storage drive as #1. I think this is the problem. Did they get turned around when I made my temporary test drive the "master"?

---

### Post by sofasurfer on 2012-01-16
I think the error message also "no device found". 
I ran...
$ sudo grub-install --recheck /dev/sdb
$ sudo update-grub

Did not change anything.
Do I need to change the order of my OS and backup drives in my menu? Can I use a copy of my grub file that I saved long ago?

---

### Post by Serpher on 2012-01-16
Are your SATA/PATA cables plugged in to the mobo in their original order? Try switching them around.

---

### Post by sofasurfer on 2012-01-16
They are in the original order. I switched them anyway. Did not make a difference.

---

### Post by techvish81 on 2012-01-16
Remove the storage drive and try to boot only with the root drive.

---

### Post by sofasurfer on 2012-01-16
I got it. I disconnected my backup drive. Now my system boots. Then I reconnected my backup drive and the system booted fine.
I don't know....
Thanks.

---

### Post by Spoiskbop on 2012-01-16
There is noticeably a bundle to learn about this here at ubuntuforums.org. I assume you made sure good factors in features also.  [buy phentermine online](http://orderphentermine.info/buy-phentermine-online) [best diet pills](http://orderphentermine.info/best-diet-pills)

---

