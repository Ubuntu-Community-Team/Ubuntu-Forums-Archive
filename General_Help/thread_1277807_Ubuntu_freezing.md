---
title: "Ubuntu freezing"
date: 2009-09-28
forum: General Help
---

### Post by dametalone on 2009-09-28
i tried ubuntu a few years ago and played with it a little.  Unfortunately i needed the hard drive space so i wiped it.  Now im a IT student and we are going to be using Ubuntu in school for our linux class so i installed it again.  

I installed the latest version on its whole dedicated drive.  I boot up into ubuntu, then i go to turn on my wifi (d link wifi card is detecting a signal from my d link router) and when i click on it, it freezes.  Cant do anything but reboot so that means no internet.  What can i do to resolve this?  


specs:

MB: Asus P5nsli
CPU:  Intel core 2 quad Q6600
Ram:  OCZ ddr2 800 4 gigs
Hard Drive: Maxtor sata 160 gig (windows 7 on other drive)

any help would be great

---

### Post by dametalone on 2009-09-28
also....i did run the live cd and got the same problem

video card:  evega geforce 8800 gt.


what i mean by freezing is......complete lock up.  you see the desktop and a cursor that doesnt move and no keyboard commands work

---

### Post by dametalone on 2009-09-28
bump

---

### Post by dametalone on 2009-10-05
ok can anybody help with this at all?

---

### Post by yeeeev on 2009-10-05
after you reboot, check out the log in /var/log/kern.log
Look for the logs before the reboot, from the time of the freeze (there are timestamp).
You can post the log content here for further assistance.

---

### Post by dametalone on 2009-10-05
> **yeeeev said:**
> after you reboot, check out the log in /var/log/kern.log
Look for the logs before the reboot, from the time of the freeze (there are timestamp).
You can post the log content here for further assistance.

i thank you for your assistance however, i have not used linux in quite some time so im back to n00b stage.  I assume i have to used command line in the terminal but what exactly do i have to type?  thank you

---

### Post by yeeeev on 2009-10-05
No problem :)
```
gedit /var/log/kern.log
```
or simply navigate to it using nautilus and double click it.
That will open the logs. Then go to the end of the logs, and just scroll up until the time of the freeze.

---

### Post by dametalone on 2009-10-05
thanks, after i get done reinstalling it, ill post my logs.  thanks again

---

### Post by dametalone on 2009-10-05
ok so i got done reinstalling it.  I even stuck in a different wifi card.  It found my wireless signal and i attempt to connect and it freezes again.  I go to reboot and now every time it starts to boot up, i think the wifi is trying to connect automatically and now i cant do anything because it is freezing too much

---

