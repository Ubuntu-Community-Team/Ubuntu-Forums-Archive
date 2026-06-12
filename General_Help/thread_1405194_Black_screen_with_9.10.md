---
title: "Black screen with 9.10"
date: 2010-02-12
forum: General Help
---

### Post by Deldo on 2010-02-12
I have problems with opening my installation of Karmic Koala.
I have tried to upgrade to 9.10 and then I can't open 9.10.
I have also tried to download 9.10, burn a CD and install it. 

By the first example, I only reach the white, blinking Ubuntu-logo and then the screen goes black, but the computer keeps running.
By the other, I press Install Ubuntu and then a lot of texts show up on the screen and again the black screen. 
It also happens if I run Ubuntu without installing it and then install it from that. I can't even try Ubuntu.

It only happens with the 9.10. I could open other versions when I tried to upgrade my way up to 9.10. 

I have an ASUS X72V, but have had succes with 9.10 before.

Please help.

---

### Post by K7522 on 2010-02-12
Sounds like a driver issue for your video card, what card do you have?

---

### Post by Deldo on 2010-02-12
nVIDIA GeForce 9650M GT; VRAM 1GB

---

### Post by severemacaw on 2010-02-12
have you installed a new video card recently? I had this same issue and it was the new card if so I may have a fix for you.

---

### Post by severemacaw on 2010-02-12
Give this a try:
Go into the computer. If you're at a black screen, press ctrl-alt-f1 to 
get to a terminal.
After logging in, type:
sudo -s
[enter your password]
cd /etc/X11
mv xorg.conf old_xorg.conf
killall gdm
exit
startx

---

### Post by Deldo on 2010-02-12
No, I have always had the same video card. But I give it a try.

---

### Post by Deldo on 2010-02-12
It didn't work. It couldn't perfom the "mv xorg.conf old_xorg.conf" and the gdm process was not found. 

So I'm still stuck.

---

### Post by Deldo on 2010-02-12
Does anyone have a idea of a solution? :-(

---

### Post by Claus7 on 2010-02-12
Hello,

card: NVIDIA 9650M GT, am I correct?

then: 190.42 glx is the package you are looking for for the drivers of your card, [http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)

and: [http://ubuntuforums.org/showthread.php?t=1300938](http://ubuntuforums.org/showthread.php?t=1300938)
a thread in ubuntu forums dealing with the same graphics card on a laptop

Regards!

---

### Post by Deldo on 2010-02-13
Now I have downloaded the driver for both Windows and Linux. 
But how do I use the one for Linux when I can't even acces a installation?

---

### Post by Claus7 on 2010-02-13
Hello,

first I have not understand fully your hdd configuration. At least I understand that you have ubuntu on one partition.

Then, when you are trying to boot from there, you find yourself to a black screen. Than means that you have a totally blackity black screen or are you able to have command line mode? If the latter you can easily install the driver.

If the former then I would suggest you to boot via the recovery mode and see what you will get.

Regards!

---

### Post by Deldo on 2010-02-13
I have to partitions. One with Vista and one with Ubuntu 9.10. But I can't acces the 9.10.

The black screen seems to be "turned off" while the computer is still running. So I can't use the terminal.

I also tried the Recovery Mode, but that didn't help.

But I found the solution. I installed the Windows-based driver that i just downloaded, and that affected Ubuntu as well. I am now writing from Karmic Koala.

---

