---
title: "Ubuntu Karmic Black Screen of Death"
date: 2009-10-31
forum: General Help
---

### Post by Ertragen on 2009-10-31
That's what I'm calling it.

I have had Now 3 Black screen lock ups with the new CLEAN INSTALL of Ubuntu 9.10 (karmic)

I CLEAN installed on my hard drive x64 version.  and installed x86 on my USB.
When I first tried x64 on my hard drive, the very first time I boot and was working
on firefox, I suddenly got a black screen lock up where only the mouse pointer
was showing.  and CAPS and SCROLL locks were blinking.

And within last half hour I was in my x86 version of ubuntu on USB drive
and THAT locked up the same way.  So I logged on again back on hard drive
and I was on this page trying to post this note, and guess what I suddenly got?
ANOTHER (the 3rd one) black screen of death.

Ubuntu Karmic - more crashes than Windows ME.

If you guys need to know,

I have SONY VAIO VGN-FW270J
x64 Intel centrino 2
4Gig RAM, 300GIG HDD
and this is NOT the first time I tried Ubuntu.  I have been using it since 6.04
and I never had this much problem this severe.  Well maybe except for the
7.04 when the screen would go all white instead during boot :D

Not good.

---

### Post by Firepowerforfreedom on 2010-01-18
Hey, I've got an old Apple PowerBook G3 (not an Intel, but a PowerPC 750 processor) with the exact same problem. For a ten year old laptop, it runs Jaunty very nicely. Give it Karmic to chew on…
  This is clearly a **universal** problem among laptops of any architecture (in other words, I haven't seen any desktops that do this), and needs to be filed as a bug. I'd do it myself, but I a) don't know how b) probably don't have enough standing in the Ubuntu community yet (have been using since September 2009). 
  Let's nip this thing in the bud and get a great Lucid release!

---

### Post by iceman600 on 2010-01-21
Im having the same issue here... i have a HP pavilion dv5-1150US. It always hung/freezes whatever you call that. Its a black screen with my caps lock blinking.

this black screen of death goes even on my laptop is on idle. 

do you think its a hardware compatibility? it all started on my laptop when i did a last update... :confused:

---

### Post by JayPeeJay on 2010-01-21
From the grub menu, highlight the normal boot option and hit "e" to edit.

Arrow down and erase "quiet splash".  I had the same issue, and only did this to figure out where it was hanging, but to my surprise just doing this alone was enough to make it boot properly!!!

To make this permanent you have to edit the /etc/default/grub.cfg file.  Doing so in gedit won't let you save the results, so u have to download the startup manager program, which I myself have yet to do but hopefully that helps.  My blackscreen of death was during the boot though, I was confused if you could boot or not from what you said.  Obviously this won't help if u get the lock up during your session.

*** update *** downloaded startup manager and added splash, but that didn't help.  I think it is because the code is bad, it just adds "splash" before the "quiet splash" which seems kinda oxymoronic, like it should either come after the "quiet splash" or just plain delete the "quiet splash".  Maybe I could edit the code of the program to make it do this?  I am kinda a noob, but I've read about scripting and think I can manage, if it will let me save! ***

*** update*** Just needed to use the gksudo command to gain access to saving the grub.cfg file.  Set both the "splash" and "quiet splash" to "", and the computer boots right up bypassing the black screen of death and showing the splash.  Go figure.  I also find it ironic that as a noob the first file that I would have to edit is the one that it says everywhere that you shouldn't edit.***

---

### Post by iceman600 on 2010-01-21
my ubuntu freezes during sessions and even on idle...
idk whats happening but i really miss my ubuntu machine

---

### Post by JayPeeJay on 2010-01-23
sorry, I guess my issue is irrelevant to the problems that you are having.  Good Luck!

---

### Post by iceman600 on 2010-02-01
found a fix.... yay!!! im having a kernel panic so i did a custom kernel and everything is running smoothly again.

if your having this problem try this fix.
[http://icemanfernnadez.blogspot.com/2010/02/black-screen-of-death-ubuntu-karmic.html](http://icemanfernnadez.blogspot.com/2010/02/black-screen-of-death-ubuntu-karmic.html)

it works for me hope it helps.

---

### Post by computerguts on 2010-02-01
I had the same prolbem, if you still want to use ubuntu 9.10 here is what you have to do, it takes about two hours but I think its worth it. 
when this happened I first had to did a hard shut down a few times which can lead to data loss and I thought that there had to be a better solution. what I did was downgrade my system to ubuntu 9.04 and went to software update and did a network install of ubuntu 9.10. It is important to leave the internet connected while you are installing the software after you have downloaded it because sometimes it needs to retrive extra packages. 

Hope this helps

---

