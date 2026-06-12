---
title: "Live Cd graphics problem"
date: 2010-05-01
forum: General Help
---

### Post by Romanrp on 2010-05-01
When I try to boot the live Cd and the instalation,they both boot fine. I can select my language and select all the other options but once the purple screen with dots stops loading I get some sort of weird image. (See attachments) This stays and I can't do anything. Please help.

---

### Post by P4man on 2010-05-01
Can you give us some details on your hardware?

Also, may sound silly, but have you tried waiting for a minute or 2-3 ? Its possible the problem only occurs during the splash screen. A live session boots rather slowly, if you havent yet, try waiting a few minutes

A last suggestion would be pressing control+alt+F1. Does that bring up a full screen terminal ? If so, try pressing control alt+F7 or F8 to go back to the gui.

---

### Post by Romanrp on 2010-05-01
thanks for the reply
My laptop is an Asus K50IN and my graphics card is nvidia G102M which is supported by all the disros I tried. Never had this problem before.
I have tried waiting for a few minutes but nothing has happened.
And yes I can go to the full screen terminal,but when I go back to GUI it's still the same.
At one point heard the ubuntu start-up noise but all I seen is the picture I posted.

---

### Post by clhsharky on 2010-05-01
HI 

Are you able to start up in safe graphics mode till you can install NV driver?

Sharky

Sorry it not installed. I had that problem with a VIA chip. Try installing from alternate CD.

---

### Post by searchfgold6789 on 2010-05-01
hey try this!
just open the cd tray up and close it again!
let us know if it works

---

### Post by Romanrp on 2010-05-01
ok I will try the cd tray method (not sure why it would work)
I am not sure how to acces the safe graphics option,when I press the F1/2/3/4/5/6 keys I get options but no safe graphic option.
I am installing from the 64bit Cd

---

### Post by Rubi1200 on 2010-05-01
I am also having issues. According to user mikewhatever:
This is a known issue according to Lucid's release notes.
[http://www.ubuntu.com/getubuntu/rele...reezes/crashes]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes")

---

### Post by clhsharky on 2010-05-01
HI Romanrp

It should be the Esc or the Tab key when booting, after BIOS of course.

Sharky

---

### Post by Romanrp on 2010-05-01
Hi sharky
I will try that now.
But before I do, Is 10.04 worth installing? Since looking at the forums a lot of people seem to be having problems.

---

### Post by searchfgold6789 on 2010-05-01
you could try 9.04 and just using update manager to climb to 10.04. That's what I did.

---

### Post by Romanrp on 2010-05-01
if nothing else works then I will try that,although I prefer a clean install but if not ,then that's life.

edit: Alternate Cd has finished downloading,now off to try everything. Wish me luck !

---

### Post by clhsharky on 2010-05-01
HI Romanrp

I do like Lucid, I haven't had any problems with lucid.
You do know NV dropped the Open Source driver and said there users can use vesa driver till there gets installed. As you can see it has caused many people trouble. Ubuntu has been trying to get the nouveau driver working by default.
Have a look here
poor bootexperiance with proprietry nvidia driver (lucid)
[http://ubuntuforums.org/showthread.php?t=1468152](http://ubuntuforums.org/showthread.php?t=1468152)

Sharky

---

### Post by Romanrp on 2010-05-01
Thanks Sharky,i tried the safe graphics boot by pressing Esc but that didn't work. Is there any way I can force the vesa driver by the command line. The cd boots fine, I can hear the ubuntu login music but too bad I can't see anything :'( .

---

### Post by benmandude on 2010-06-10
I had the same problem as you, add "xforcevesa" without the quotes to the bootline from the menu by pushing tab to edit boot option.

---

