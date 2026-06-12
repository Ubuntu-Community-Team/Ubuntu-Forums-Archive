---
title: "Ubuntu Brightness"
date: 2012-03-03
forum: General Help
---

### Post by Donavon on 2012-03-03
So I've pretty much fixed my problem, however when I login, I get a black screen, but I can hear the login music.

I have an HP Omni 120-1026 Desktop PC, so there is no place on my computer, nor my keyboard to raise the brightness.

I installed Ubuntu within windows, so in the Ubuntu folder, is there a line I could edit to raise/set the brightness? 

Thanks

---

### Post by Frogs Hair on 2012-03-03
This happened to me on my first try with Ubuntu and it was due to the video driver and not the brightness . It may be possible to install the driver from the recovery console if you know what kind of video card you have .

I got lucky after a few boot attempts and was able get the GUI up and install the driver .This was back on a Wubi 9.10 installation and I have not had the problem since.

---

### Post by Donavon on 2012-03-03
I can't get into recovery console, cause I haven't installed it (sorry if I said I did) - I was trying the demo.
If I try to install it, a bunch of text comes up on a black screen, then it goes blank. 
I do hear the login sound when I try the demo, but there is no picture.

---

### Post by Donavon on 2012-03-03
small bump - still in major need of help

Help will be greatly appreciated.

---

### Post by raja.genupula on 2012-03-03
have you tried this ?

[http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/](http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/)

---

### Post by Donavon on 2012-03-03
Thanks for the reply

Yes, I've tried that - along with i915.modeset=1 and 2, xforcevesa, radeon.modeset=0, nomodeset.

I am trying to install it inside windows 7. I ran the exe, then it had me restart computer.  on the menu clicked "demo mode" (but before I clicked it I changed "quiet splash" to nomodeset.  Then after that I get a black screen, and I can hear the little sound it makes when it logs in. Also, if I click the volume buttons on my keyboard, i can hear it making the sounds turning it up.

I really don't know what to do

---

### Post by Donavon on 2012-03-04
bump

---

### Post by Donavon on 2012-03-04
any help?..

---

### Post by raja.genupula on 2012-03-05
Its looking like graphic drivers issue , 
> I installed Ubuntu  within windows, so in the Ubuntu folder, is there a line I could edit to  raise/set the brightness? please boot into recovery mode and then choose failsafeX and from there reinstall your graphics drivers . 

and as you asked for brightness 
  [http://superuser.com/questions/96539/how-do-i-adjust-display-contrast-and-brightness-in-ubuntu](http://superuser.com/questions/96539/how-do-i-adjust-display-contrast-and-brightness-in-ubuntu)

PLEASE DONT BUMP SO EARLY . GIVE US TIME .  :grin:

---

### Post by cariboo on 2012-03-05
Please don't bump your threads more than once every 24 hours. 

What graphics chipset does your system use?

---

