---
title: "HELP try hd1,0 no wibildr"
date: 2010-05-19
forum: General Help
---

### Post by pnx031 on 2010-05-19
Hey guys,

I've been trying for days to install ubuntu 10.04. 

Firstly I got the msg that Try hd1,0 NTFS5 no wibildr which I found in the forums was a common problem. I waited and waited and it wouldn't boot to grub. I tried reinstalling and it didn't do any difference. I tried changing the position of the files from the boot folder into the ubuntu folder where the installation was found and it booted and then gave me a black screen where there were commands to insert etc.

I checked the folder size of grub and it shows 0kb. 

I don't know what else to do.

I have Win 7 and Win Vista installed already and was trying to put ubuntu on top using wubi. I have an empty 30gb partition for ubuntu and it still doesn't work.

---

### Post by pnx031 on 2010-05-19
and just to mention.
When I install from a cd, the installation fails initially and boots me into the live version of ubuntu.
If I extract everything and install the installation takes 10 seconds.
If I mount the image it takes 2 minutes to install.
Somehow I do not think ubuntu are installed properly

---

### Post by pnx031 on 2010-05-20
bump

---

### Post by bumanie on 2010-05-20
I am a bit lost with what you are trying to do, as in is it a wubi installation or an installation to a separate partition. Here is a good [tutorial]("http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml") for installing lucid - read it and see if it helps answers you query. If the tutorial is not helpful, post again.

---

### Post by pnx031 on 2010-05-20
Alright from the beginning then.

-> I downloaded the 64 bit version of ubuntu and burned it on a cd.
-> I tried to install it and the installation failed. It booted into the live version of the ubuntu on the cd instead.
-> Then I extracted the .iso and installed it from windows.
-> Tried to boot and got the try hd 1,0 NTSF5 no wibildr error. Waited and still didn't boot.
-> I looked into the problem on forums etc and no1 seems to be having the same problem because:
a) When I moved the wibildr file into the ubuntu folder in the seperate H partition (31 Gbs) that I created just for ubuntu
b) it did try to boot but it didn't manage to find GRUB, and it failed again giving me a black screen.
-> booted in windows again, relooked into the problem and checked the grub folder which is empty and has 0kb of data in.

In my opinion it seems like there is no installation data being put into the folders when I run the wubi installation. 

I do not know what else to do any thoughts?

---

### Post by pnx031 on 2010-05-20
my pc is an AMD 64 quad core and it already has vista and win 7 installed on. Also it is not my first attempt to install ubuntu. I tried them before years but never had any problems like this.

Any ideas?
I am going to download the 32bit version and try again.

---

### Post by Mark Phelps on 2010-05-21
You may be wasting your time with Wubi 10.04.

To see if that's true, you need to go to the Installations subforum and read through the Testing Wubi 10.04 thread.

There may be posts there dealing with your problem and providing solutions.

Otherwise, you just might have to wait until they actually get Wubi 10.04 working.

---

