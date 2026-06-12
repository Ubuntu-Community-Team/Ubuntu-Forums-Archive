---
title: "Cant burn files to DVD-R, please help?"
date: 2010-06-18
forum: General Help
---

### Post by Lookabird on 2010-06-18
Hi guys, 1st time to linux. I have ubuntu 10.4 installed, everything works on my Toshiba A200-TJ9 laptop except for the built in webcam and mic, as well as the DVD burning function of my multi drive. The drive itself is a HD-DVD Rom with CD/DVD +/- R/RW capabilities. I did a $sudo cdrecord -scanbus and it shows:
scsibus0:
0,0,0     0)'Toshiba' "DVDW/HD TS-L802A" "TO35" Removable CD-ROM
0,1,0     1)*
0,2,0     2)*
0,3,0     3)*
0,4,0     4)*
0,5,0     5)*
0,6,0     6)*
0,7,0     7)*

Beyond that i know absolutely nothing, and when i put in a blank CD or DVD -R, it shows up as a blank CD/DVD-R, but its properties show as 0 bytes used, 0 bytes free and 0 bytes for capacity. And not surprisingly, Brasero says not enough disc capacity when i try to burn a 2.7 gig file onto the DVD-R. 
Any help is greatly appreciated

---

### Post by Sin@Sin-Sacrifice on 2010-06-18
Try gnomebaker... you can find it in synaptic you type ```
sudo apt-get install gnomebaker
``` in the terminal.

---

### Post by Lookabird on 2010-06-18
> **Sin@Sin-Sacrifice said:**
> Try gnomebaker... you can find it in synaptic you type ```
sudo apt-get install gnomebaker
``` in the terminal.

Thanks Sin, its burning now, appreciate the help :D

---

### Post by Deadite81 on 2010-06-18
This is interesting, I had the same problem.  Get this - using Brasero with my fresh 10.04 install I put a blank DVD in and it read 0 bytes. 
 Using K3b (KDE burner) the DVD was read correctly.  
Go back to Brasero...0 bytes.  
So I tried a CD.  Brasero = 0, K3b good.  
So I tried a *different* blank CD & DVD and Brasero read them correctly....But no matter how many times I tried or rebooted, it would not read those 1st discs correctly.  The actual physical first two discs.  That makes **Absolutely No Sense**, but it's what happened, over and over again.  I threw those discs away, good or not, they were possessed.

After those fist discs, however, Brasero has never given me a problem.  I have 2 HP DVD burners, 1 external and 1 internal, neither HD though, and both have worked fine since.

I don't know much about this particular subject, but I do know that Brasero gives a lot of people problems.  You could try another program, Gnome CD Master perhaps, and see what it does.  It and many other burning applications are available in the Ubuntu Software Center.  They are generally small and you can always remove them later.

A question though: Is your drive able to play DVDs and CDs?  If the answer is yes, there's a good chance it's Brasero crapping out, not Ubuntu failing to pass the correct info along.

---

### Post by Lookabird on 2010-06-18
> **Deadite81 said:**
> This is interesting, I had the same problem.  Get this - using Brasero with my fresh 10.04 install I put a blank DVD in and it read 0 bytes. 
 Using K3b (KDE burner) the DVD was read correctly.  
Go back to Brasero...0 bytes.  
So I tried a CD.  Brasero = 0, K3b good.  
So I tried a *different* blank CD & DVD and Brasero read them correctly....But no matter how many times I tried or rebooted, it would not read those 1st discs correctly.  The actual physical first two discs.  That makes **Absolutely No Sense**, but it's what happened, over and over again.  I threw those discs away, good or not, they were possessed.

After those fist discs, however, Brasero has never given me a ere's a good chance it's Brasero crapping out, not Ubuntu failing to pass the correct info along.problem.  I have 2 HP DVD burners, 1 external and 1 internal, neither HD though, and both have worked fine since.

I don't know much about this particular subject, but I do know that Brasero gives a lot of people problems.  You could try another program, Gnome CD Master perhaps, and see what it does.  It and many other burning applications are available in the Ubuntu Software Center.  They are generally small and you can always remove them later.

A question though: Is your drive able to play DVDs and CDs?  If the answer is yes, there's a good chance it's Brasero crapping out, not Ubuntu failing to pass the correct info along.

Deadite81, my drive is capable of playing DVDs, CDs, as well as HD-DVDs. Bought the laptop from Toshiba at a huge discount (50% off) when they realized that HD-DVD was gonna lose to blueray. And yeah, with Brasero, it wont recognize ANY of my CD-Rs nor DVD-Rs, and I have a Frankenstein of a spindle of like 75 DVD-Rs and CD-Rs from 5 different brands, and none of them registers...

---

### Post by Deadite81 on 2010-06-18
Well, that's Linux for you.  Can't win 'em all.  At least it's working now (didn't see Sin's post before I posted:)).  A cool program I use is called Gnormalize.  It converts, burns and more all in one and has worked well for me, especially concerning music.  Never used Gnome Bake, heard it's good though.  I'd have probably bought the laptop too...50% off is 50% off, HD or not!

---

