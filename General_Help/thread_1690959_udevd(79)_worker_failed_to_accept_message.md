---
title: "udevd(79) worker failed to accept message"
date: 2011-02-19
forum: General Help
---

### Post by juliancam on 2011-02-19
Hi I am getting this message:

udevd (79) - (3 numbers that increase with each attempt) - worker failed to accept message - kill it

about 7 out of every 10 times that I boot. The message normally appears about 8 or 10 times then Ubuntu proceeds to load and work normally. Originally I was getting the message 

...... worker failed to launch - kill it

but this changed after I tried recovery mode and repair broken packages. Now I am still very unknowledgable (if there is such a word) about Ubuntu and I don't even know what is failing. It started after I tried to tweek the system for problems with video playback but I can't remember which forum post I was following to remember what I changed.

I assume there is some way to to get Ubuntu to save a log of its boot processes so that I can see what process is failing and do a search for how to cure it. However I have had little luck in searching Google for this procedure - I assume I am using the wrong phrases. Please can someone give me an idiots guide on how to set this up.



Julian

---

### Post by sugarland2k on 2011-02-22
Getting this udevd error message on boot on my Dell Mini 9 (Xubuntu 10.10.1 Xfce) also!  I am looking for a solution, will advise if I find one.

---

### Post by sugarland2k on 2011-02-23
this code fixed the udevd boot error on my Mini 9 with Xbuntu 10.10 Xfce


echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 
sudo update-initramfs -u


Good Luck !!!

---

### Post by bbp on 2011-03-20
@sugarland2k Thanks, it works for me. There were probably no side effect related with it, but I like to have a nice boot screen :popcorn:

---

### Post by hanson53 on 2011-03-25
Hi, I am new to Linux and am using Ubuntu 10.10 Netbook edition on an Acer Aspire One ZG5 and I also get this error message but would like to have a clean boot screen. The solution sounds simple enough but is unclear to me as a new user.

Is the solution to be copied and pasted into a file? If so what is the name and location of the file.

Or do I only have to apply those commands once in a terminal screen?

Thanks in anticipation

---

### Post by hanson53 on 2011-03-28
OK problem solved - run the commands in a Terminal window. An error message was displayed when running the sudo update command
:
6: Can't open /scripts/casper-functions

However, the udevd(79) problem has gone on bootup :D

Thanks

---

### Post by xiioiv on 2011-04-09
Same issue, same result after using commands.... 
no more error messages on startup.
Thank you.
I hate error messages before you start your work day

---

