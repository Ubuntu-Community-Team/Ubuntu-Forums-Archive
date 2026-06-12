---
title: "Ubuntu boots fine,  totally random time limit then black screen, mouse pointer frozen"
date: 2011-06-08
forum: General Help
---

### Post by ashz on 2011-06-08
Hi All,

Used to be a long time user of Ubuntu, recently got a new laptop and decided that I wanted to go back to the world of Ubuntu and installed Maverick on my system and then updated to Natty  when it was released, was perfectly fine until Sunday (ish) when I updated (Looks like it updated Xserver and Python).

Okay so the problem is this, I am using a Dell Laptop, I3 Processor, Intel Graphics with 3GB of RAM, 320GB HDD, N510 model.  Ubuntu is Dual Booting with Windoze 7 oh and I have a Microsoft Blue Laser Wireless Mouse attached.  Since the weekend I have had an issue that it will randomly go to a black screen with the mouse pointer unable to move.  It does not respond to anything and I have to turn off via the power button.

I can surf the net with Firefox for example and all is fine, the issue I have is if I start up Deluge (Bittorrent) with a few minutes black screen no mouse, so I decided to be sneaky, or so I thought, and installed qtorrent thinking it was an issue with Deluge, all seemed fine for 5 mins then BAM...black screen no mouse had to do hard reset.

Well if anyone can help and they wish copies of any logs then please state command to get such logs and they will be yours.

Please save me I dont wanna use Windoze :(

Edit:Forgot to mention I am using the 64Bit Version of Natty

Cheers

Ash

---

### Post by ashz on 2011-06-08
Anyone?

---

### Post by cbecker78 on 2011-06-08
Try turning off your screen saver maybe?  Can you use "top" in a terminal while downloading to watch what sort of memory and processor time is being consumed just before the black screen?

Is your PC Hot?  If the fan is not working, it can force an emergency shutdown or lock up if overheating.

Also, it is better to restart a frozen system by holdint down "control" and then slowly pushing SysRq(print screen), R, E, I, S, U, B...  This provides a soft shutdown that gives your OS a chance to unmount and exit hung programs.  It is less likely to corrupt your system than a hard-shutdown with the power switch.

---

### Post by ashz on 2011-06-09
Thanks for the reply Cbecker,

Screen Saver is off, first thing I tried

PC Temp is fine

And I never knew that about a soft reset...you learn something everyday :D

I disconnected the wireless receiver for the MS Mouse and reconnected again and though I am not too sure why that seems to have fixed the problem.. well it has not randomly frozen yet...give it time :P

Thanks again for your help though much appreciated,

Ash

---

