---
title: "Linux Drivers"
date: 2011-04-23
forum: General Help
---

### Post by jon2718 on 2011-04-23
Hi,

I am building a linux box using a Zotac H67 mini-itx motherboard.  This motherboard has onboard wifi, integrated graphics and networking.  It uses the Intel H67 chipset.  Before I build this, I want to make sure I can get Linux drivers for it.  Does anyone know how I can find this information and where?

Thanks in advance.

-Jon

---

### Post by KegHead on 2011-04-23
Hi!

Your specs look ok.

[http://www.itxgamer.com/motherboards/zotac-h67-itx-wifi/](http://www.itxgamer.com/motherboards/zotac-h67-itx-wifi/)

What type of hd?   SSD?

KegHead

---

### Post by jon2718 on 2011-04-23
Hi,

I haven't decided on HD.  How and where do I find the drivers that will support linux on this board?  Is there a place you can direct me?

Thanks.

-Jon

---

### Post by KegHead on 2011-04-23
Hi!

Drivers for what?

Video?

KegHead

---

### Post by jon2718 on 2011-04-23
Hi,

I need drivers for video, networking and wifi.  I am not sure exactly all the drivers I will need for that board, but certainly video and wifi.  I think I will need drivers for the networking but I'm not sure.  I haven't done this before so I don't know how to find the information I need.

Hope you can help.

Thanks.

-Jon

---

### Post by 3rdalbum on 2011-04-23
> **jon2718 said:**
> Hi,

I need drivers for video, networking and wifi.

Video and networking will be included in Ubuntu. Wifi might be too - look up the chipset model number of the wifi and the word "ubuntu" to see if it will work, i.e.

"RTL8187 ubuntu". <- Google.

---

### Post by jon2718 on 2011-04-24
Hi,

Thanks for your help.  I had a general question.  If I am considering a particular motherboard, how do I know what drivers are required for Linux support.  And, where do I go to download the required drivers once I know what they are?

-Jon

---

### Post by cchhrriiss121212 on 2011-04-24
Hello Jon,
For most Linux distros you do not need to go to a website and manually download drivers for all this stuff, it will be included with the OS with no config required. 
Sometimes a certain wireless chip might not have an open source driver (which means it cannot legally be included with the OS), so you will need to plug it in to a wired connection and use Ubuntu's "Hardware Drivers" utility to download it. 
Nice, eh?

This approach has downsides however:
In your case you have a relatively new board, which means that you will need a relatively new distro to get the latest drivers. So hardware released in 2011 (like sandybridge graphics) will not be compatible with an Ubuntu version released in 2010 (like 10.04).

So in practical terms: install 11.04 when it comes out and you should be OK. Intel are pretty good with Linux support, and all their wireless chips work nicely, a few GPUs were problematic years back, but this new line has drivers being included into Ubuntu 11.04.

To answer your general question about finding compatible mobos, just google the board number together with "Linux" or "ubuntu". No need to get involved researching every driver the board will require, the search results will show you if the hardware works or not.

---

