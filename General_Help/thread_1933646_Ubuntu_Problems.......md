---
title: "Ubuntu Problems......"
date: 2012-02-29
forum: General Help
---

### Post by HoneyBadger1 on 2012-02-29
Guys I just installed Ubuntu 10.04 last night and I have been struggling to get it to work.

Here are my current misfortunes:

1.) Ubuntu won't use my built in speakers(I can use headphones just fine though.)
2.) Microphone wont work
3.) Wont detect my wireless card.(To get around this I am using a USB  wireless adapter....but still, it would be nice to use the one built in  the computer.)

I am using a HP Touchsmart 300-1020

---

### Post by HoneyBadger1 on 2012-02-29
anyone? :-(

---

### Post by DaimyoKirby on 2012-02-29
Have you tried updating the drivers for the specific hardware that is inside your computer?
I suppose since it's an all-in-one, you haven't switched anything out, so you'll just have to look up the specs to find out what's inside, then google for the drivers.

Past that, I'm not really sure how you'd go about fixing it...sorry.

---

### Post by HoneyBadger1 on 2012-02-29
> **DaimyoKirby said:**
> Have you tried updating the drivers for the specific hardware that is inside your computer?
I suppose since it's an all-in-one, you haven't switched anything out, so you'll just have to look up the specs to find out what's inside, then google for the drivers.

Past that, I'm not really sure how you'd go about fixing it...sorry.


Thanks Daimyo, I downloaded all the drivers for my Hp Touchsmart from here:

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=4007375#N317](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=4007375#N317)

I just can't install them because they were made for Windows 7.
is there a way I can install them in Ubuntu?

---

### Post by evilbrent on 2012-02-29
google for ndiswrapper.
 
ndiswrapper is the way that ubuntu uses windows drivers.

---

### Post by UltimateCat on 2012-02-29
Hi:
This should be helful:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

And once you know which NIC Network Interface Card you have you should be able to find the driver to accommodate your card.

Some NIC sites
[http://sourceforge.net/](http://sourceforge.net/)

[http://www.driverupdate.net/new_lp/realtek_lp.php](http://www.driverupdate.net/new_lp/realtek_lp.php)

I had to black list the rtl8169 in order for my Ndiswrapper in my Ubuntu 10.04 to work....
Hope this helps

---

### Post by HoneyBadger1 on 2012-02-29
thanks guys I'am going to try it.

---

### Post by jerome1232 on 2012-02-29
What have you done regarding your speakers, have you tried utilizing the sound gui to swap between the various outputs of your sound device? (click on the speaker icon in the top right, click sound settings, and click the various devices and outputs listed, testing speakers each time to find the right one)

---

### Post by raja.genupula on 2012-02-29
Yeah Got one more thing for you 
look at this if  you got any problem 
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

