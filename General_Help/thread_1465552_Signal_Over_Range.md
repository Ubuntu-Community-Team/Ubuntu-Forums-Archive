---
title: "Signal Over Range"
date: 2010-04-29
forum: General Help
---

### Post by danisgood on 2010-04-29
Hi,

Firstly, I'm not a expert, so could you try to put any solutions into plain English please.

I have tried to install Ubuntu 10.04, however I receive the "Signal Over Range!" message on my TFT monitor. On the live cd, I had to press F6 and nomodeset to run Ubuntu to install it. However, now it is installed, upon boot, after the GRUB boot menu, after selecting Ubuntu, I just get the "Signal Over Range!" message, and cannot continue. 

Can someone please help.

---

### Post by spartan7 on 2010-08-28
Im getting the same thing with a wise wing flat lcd screen.

PC= pavillion a1610n with nvidia graphics card.

Anyone have a fix? 

* I fixed this before by using a different screen. sucks I dont have one now :(

---

### Post by anotherbigal on 2010-09-05
Hi spartan7

I know that this post is a long time after yours but I found it after I had the same problem.

I usually use CentOS as my flavor of Linux but thought that I would have a look at Ubunty on a spare machine that someone gave me. It is quite old but I thought good as a test bed. When I tried to install 10.1 I had the same problem so tried an earlier version, 7.1.  In CentOS the graphics are controled via a file called xorg.conf. I would look for that in the /etx/X11 directory. You have to be 'root' (superuser) to edit it. 7.1 installed ok so I thought great. It all went wrong whern I got to the first boot. The one without the disk in. That was where I ended up with the same error message.

I solved it the'buy a new part' way. As I said, I was installing it on an old machine. The graphics card was  an old one with virtually no memory. I put a replacement one with 256 MB of memory and then I was away. Both the original and new cards use nvida drivers  and to be honest I believe that it is a driver problem but I don't know enough about it to sort that out. I found my card on Amazon and as it is not a serious gaming card it cost just under £35.00 including £5.00 delivery.

Anyway, good luck with you system. Please come back and let us know how you got on, or if you gave up.

Cheers

Alan

---

