---
title: "I need help to resort the GRUB boot list"
date: 2010-08-07
forum: General Help
---

### Post by LindseyS on 2010-08-07
I have tried to find my answer by searching around the web but I am afraid I can't figure it out and need to enlist the help of someone smarter then me.

I installed Ubuntu on my machine as a dual boot with windows xp.  The thing is that I want to have windows XP be the machine at the top of the list so that when I click the power button that it will automatically be chosen as the default os of choice, rather then Ubuntu which is not the automatic os to be booted up unless someone is there to push the down arrow button at just the right time.  This has put quite a strain on our marriage as my wife really dislikes that it is set up this way.  


So I am showing a screen shot to help clarify what I am after,  In the list below,  I want Windows XP to be at the top of the list,  Anyone know how to achieve this?


[IMG]https://sites.google.com/site/ifollowhim/home/IMAG0177.jpg[/IMG]
[IMG]http://picasaweb.google.com/Ifollowhim/Web#slideshow/5502762585722252610[/IMG]

---

### Post by Mark Phelps on 2010-08-07
If your'e running legacy GRUB, there will be a menu.lst file in your /boot/grub folder.

In that file, there will be a line near the top that will have "default 0" in it.

Change the "0" to the number indicating the stanza you want to be the default.  For example, if it's the fourth one in your file (each stanza starts with a "title" line, you change the zero to a 3.

Edit the file by entering "gksudo gedit /boot/grub/menu.lst" and providing the root password.

---

### Post by LindseyS on 2010-08-07
Thank you,  that worked like a charm.  When I first read your instructions I was like, does this guy know how little I know about Linux, but then when I dug in and followed them, they made sense and I was able to get it changed.

thanks again for your quick response!

---

