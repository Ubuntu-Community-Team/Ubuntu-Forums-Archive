---
title: "New Ubuntu install has trouble booting"
date: 2009-11-11
forum: General Help
---

### Post by jetsetlemming on 2009-11-11
The day before yesterday I installed the latest version of Ubuntu, 9.10. Ever since, however, I have been having problems with the install managing to boot. I've managed to get through twice since the initial install, after many attempts and looking in vain through different options (I'm completely new to this stuff, and don't really know what I'd be looking for to change in the first place).
The typical behavior is to show the white Ubuntu logo, quickly splash some text in the top left corner too quickly for me to read, a blinking _ prompt for a couple seconds, and where in a successful boot the mouse cursor and then the Ubuntu splash screen would appear, I get absolutely nothing. Just a big blank screen that I can't interact with at all. 
I've run memtest, fsck, and checked the integrity of my Ubuntu disc, all came back clean. 
The Live CD can load just fine every time, it's how I've tried to find out information on the problem and get help so far, though all that's come up is basically how to run fsck, how to find syslog, and that there's a critical error with Intel 8 chipsets in the current version that occasionally causes freezing in already running Ubuntu.

Here's a pastebin of my syslog:
[http://pastebin.com/m3bca2464](http://pastebin.com/m3bca2464)

System stats:
Intel Celeron 2.4 Ghz Processor
1GB DDR1 RAM
40GB PATA HD
Intel 828 video
SoundMAX audio
Ubuntu 9.10, just downloaded and installed two days ago, and currently up to date according to the update tool.


Launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/483451](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/483451)

---

### Post by jetsetlemming on 2009-11-11
I've found that I can get into my hard drive install through the Live CD with the "boot first hard drive install" option on the Live CD's menu. 
I would assume this means there's a problem with GRUB on my system, or something? Can I repair install that/update it?

---

### Post by prabath_fun on 2009-11-11
I also faced almost same problem. I believe that, I got this problem after I installing VLC media player.
  If any body found solution, please update...
Prabath

---

### Post by Scott30101 on 2009-11-11
Good God this is a serious error we are facing!  Someone please help, I'm going crazy

---

### Post by jetsetlemming on 2009-11-14
[http://pastebin.com/m130cc8fd](http://pastebin.com/m130cc8fd)

Pastebin of a segment of syslog specifically from a failed boot attempt. 

I was looking at the bugs reported for Ubuntu, and thought the issue in this thread might be related to this:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/68012](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/68012)
However, my BIOS setting is for 8MB of video memory buffer, so there should be enoguh vram. However, once I boot into ubuntu, via the livecd "boot first hard disk" option, I see it's only assigning 8MB of Vram to my integrated graphics. I don't know how it behaves differently from windows, but in windows a setting of 1MB vram buffer resulted in 8MB real Vram, and 8MB buffer in 64MB Vram. This is a significant difference in performance and space to work in. 
Is the issue perhaps that Ubuntu/Grub is ignoring my/our BIOS integrated video buffer setting?

---

### Post by singercs on 2009-11-14
I too installed the newest version from 9.04 and couldn't get the machine to boot without using the disc, I tried everything but finally after the fourth install I went back to the site and downloaded 8.04.3 and did the install again and now everything works and I am now a happy camper again.
Also, when the 9,10 version was installed and I could use it, I had no cd/dvd or floppy, which I had before so anyway, all is well now and I am not going to install 9.10 on any of my units until the bugs are gone.

---

### Post by inearlygaveup on 2009-11-14
I have also had big access problems with 9.10.

I am just about to re-install 9.04.

I did get 9.10 running on a few occasions and was impressed ..........BUT having to try and log in for over five attempts each time, has finally made me give up.
especially as 9.10 was set to auto login. I will try again in a few months.

---

### Post by jetsetlemming on 2009-11-20
I managed to fix this by forcing Grub 2 (which is the Karmic version of grub) to update itself. I was installing Windows XP and going through the steps to fix dual booting, and it seems like the fix was just coincidental. You other guys who have experienced this try:
sudo update-grub

I can't find the page I was on with the full instructions, which included commands to automatically probe the available partitions for OS's, create grub boot options for all of them, and THEN update grub, I'm still looking. That command alone might work though.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Edit: Nevermind. It failed on a second boot, still need the LiveCD to get it to work. :( Guess whatever changed that made it work gets reset as ubuntu loads.

---

### Post by prabath_fun on 2009-12-02
Hi,
   I thought of giving one more try and installeded (with wubi) day before yesterday. Even, I installded VLC same day and restarted again and again. I found zero problem. Yesterday, as well, I installded some of the new packages and restarted again and again. No problem. I don't know, why earlier I got some problem. 

Also, I was facing difficulty to enable 5.1 surround and got it solved.

Now, I am very happy user of Ubuntu9.10 and thanks to canonical / Ubuntu team.

---

