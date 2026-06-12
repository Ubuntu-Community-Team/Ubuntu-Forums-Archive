---
title: "Ubuntu 8.04.2 on Dell Mini not booting"
date: 2009-12-13
forum: General Help
---

### Post by Malq on 2009-12-13
Hi folks, I have a real problem with my daughters dell mini 910. She was complaining about slow internet speeds and unable to connect to our home network. I know nothing of Ubuntu, I have looked at it a few times but got scared off!! This time I was able to sort out the network connection. I was then informed that there were updates available and so I downloaded them, it took quite a while and there were a few warnings of updates not downloaded. The updates then installed automatically, it looked like it would take a while so I left it overnight. When I was tinkering around I noticed that one of the drives was sitting at 99% used. I decided to delete some applications that my daughter would not need. Did this through the add remove programs. Also used the synaptics manager to remove some other programs. To cut a v long story short the machine will not boot!! On boot up I get the ubuntu splash screen with the progress bar, the bar fills up and then I get:
 
usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600
 
Ubuntu 8.04.2 elle_Note tty1
 
elle_Note login:
 
I can login ok, the output from fdisk -l is:
/dev/sda1 1 8 32224+ de Dell Utility
/dev/sda2 * 9 917 3665088 83 Linux
 
I know absolutely nothing about ubuntu I am afraid, (as shown earlier!!) I have read through loads of earlier posts but none seem relevant to my problem. One thing I did try as suggested in one thread was
sudo dpkg-reconfigure xserver-xorg
output was /usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed
 
Don't know if this helps or just messes things up.
The dell mini has a 4Gig SSD, no dvd/cd and it did not come with any disks at all. Thanks in advance for any help offered. Apologies for the length of this post.:D

---

### Post by 3Miro on 2009-12-14
Hi,

there are some things that I am not getting right.

1. If the computer has no CD/DVD how did you install Ubuntu in the first place? What do you have to work with?

2. You are saying that the computer doesn't boot, however, you then say that you can log in. Is it that the computer doesn't boot or that it only boots to console (i.e. you can type but no mouse/menus).

Do you know what kind of video card the computer has? Is the 4GB ssd the only hard drive that you have?

---

### Post by snowpine on 2009-12-14
Hi Malq, as a fellow Dell Mini 9 owner, I feel your pain! The pre-installed "Dell Ubuntu Remix 8.04" is not very good (in my opinion). It is outdated (8.04=April 2008) and not well maintained by Dell (updates have a way of breaking things). Also, 4gb is pathetically small (Ubuntu recommends 8gb minimum) yet Dell seems to have disregarded this limitation in their updates.

Unfortunately I can't help you troubleshoot the problem, since I no longer use "Dellbuntu" on my Mini. Here is the site I used to install the current version of "regular" Ubuntu on my mini: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by Malq on 2009-12-16
Hi 3Miro,
Apologies for taking so long to reply. In answer to your questions;
1. Mini came with Ubuntu pre loaded, there are 3 USB ports, a flash mem card reader and a 10/100 ethernet port
2. Again apology, it boots to tty1, console.
3. Yes 4 Gig SSD only drive. Glossy 8.9" (22.6 cm) 1024x600 LCD.
 
Mal

---

### Post by Malq on 2009-12-16
Hi Snowpine,
Thanks for your reply. It is my daughters machine and I don't think she intended to get the Ubuntu version as she has a win desktop. I was looking forward to playing around with Ubuntu as I have previously attempted to install it on an old desktop I have lying around. I am reasonably au fait with windows but Ubuntu just seems like a lot of hard work to get it to look and feel right. I intend to persevere and will look at the link as soon as I get a chance. Thanks again.
Mal

---

### Post by t0p on 2009-12-16
Sorry OP, no helpful hints on your immediate problem (except some untimely advice: don't delete system files from your daughter's computer ;) ).  

I also have some more constructive advice for when you reinstall/upgrade: my EeePC also has a 4GB SSD, which isn't really enough to run Ubuntu.  But my machine also has a built-in SD card reader and a number of USB ports.  I have a 4GB SD card permanently mounted in the reader, and when I installed Ubuntu I put the /home directory in a separate partition of its own, on the SD card.  I also frequently save files to USB sticks so less room is used up on the precious SSD.

---

### Post by tux821 on 2009-12-16
Hello Malq,


I have Ubuntu running on my netbook (Acer Aspire One with 8G SSD) for some time now and am very happy with the performance and easy install.
What I should do is install the new Ubuntu 9.10 Karmic Koala netbook remix version from USB.
Your version 8.04 is very old, newer Ubuntu versions always get newer drivers and improvements. Most of the feedback I have seen now on the new 9.10 netbook remix version are very positive. For me it installed out of the box, everything working, not a single problem. 

It's not that difficult to install with an USB stick, see:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

and as posted earlier:
[http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html)

For me this 9.10 version install size was about 2.5G so it should fit easily on your Dell SSD.

---

### Post by Malq on 2009-12-16
Cheers t0p, untimely but wise indeed!! In my ignorance I thought that the 4G would have been plenty of space as all she wants it for is browsing the web. I was amazed to find that prior to me deleting the files there was no space, i.e. the disk was sitting at 99% full. I don't fully understand the drive structure at the mommet but some light reading will hopefully change that. This Ubuntu stuff is not as easy as I thought it was going to be. Every day is a learning day!!

---

