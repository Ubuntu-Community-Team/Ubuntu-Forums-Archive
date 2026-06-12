---
title: "Several problems with lubuntu running on an old laptop"
date: 2012-07-31
forum: General Help
---

### Post by ceciliasp on 2012-07-31
Hi!

I'm already using Uuntu 12.04 on my lenovo Ideapad G550 and I'm having a great time learning about linux. Mi husban has an old Compaq Presario X100 Intel Centrino with 256 mb ram, he uses it to connect to the internet, browse and sometimes use a word processor.
I was trying to run lubuntu from a USB Stick (Lubuntu 12.0.4) so I could test the performance (given the low hardware spec) and I faced a few issues:
At start up, when I'm given the options I select "Live" or "Persisten" and It takes for ever to start. Whem I say for ever, I mean like 10 minutes.
After that, I could not get the wireless card to work. It is a Intel Pro Wireless 2100. I tried an external usb wireless adapter and could make it run just fine.
Apart from that, I restarted the computer and now I see a strange messege (on a black screen) taht says:
"Stopping enable remaining boot-time encrypted block devices".

really don't know what that means...
Any help will be appreciated.
Thanks
Cecilia
Argentina

---

### Post by Rodney9 on 2012-07-31
A CD may work better, you can run it as Live to check if everything works before installing.

For USB see here - [http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Lubuntu is perfect for old machines like yours.

For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by TheFu on 2012-07-31
It is hard to tell from the description, but this thread [http://ubuntuforums.org/showthread.php?t=1744169](http://ubuntuforums.org/showthread.php?t=1744169) has the same message (which could be completely unimportant) 

He ended up booting into failsafeX mode and reloading the ATI graphics driver. [http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html](http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html) has instructions, but this may not have anything to do with your specific issue.

---

### Post by tartalo on 2012-07-31
A Live CD /USB (Try without installing) will boot and perform quite slower than an actual installation, specially if the computer doesn't have a lot of RAM. That's because Live CDs load a compressed filesystem to RAM. More info: [https://en.wikipedia.org/wiki/Live_CD](https://en.wikipedia.org/wiki/Live_CD)

However, you might achieve a satisfactory performance with a Live distro like Puppy Linux, because it's designed with very low spec computers in mind (In fact they encourage not installing it): [http://puppylinux.org/](http://puppylinux.org/)

---

### Post by krakenchaos on 2012-08-01
I'm using lubuntu from 8Gb thumbdrive on Presario V200 right now. So far so good. Quite smooth. But my laptop has 1Gb of ram.

To speed up things a little bit, you should install OS to thumbdrive but not as a live USB.

---

### Post by maxpro4u on 2012-08-15
> **krakenchaos said:**
> I'm using lubuntu from 8Gb thumbdrive on Presario V200 right now. So far so good. Quite smooth. But my laptop has 1Gb of ram.

To speed up things a little bit, you should install OS to thumbdrive but not as a live USB.

I don't think the OP's laptop is able to boot from USB.

---

### Post by quadproc on 2012-08-15
> **ceciliasp said:**
> Hi!

I'm already using Uuntu 12.04 on my lenovo Ideapad G550 and I'm having a great time learning about linux. Mi husban has an old Compaq Presario X100 Intel Centrino with 256 mb ram, he uses it to connect to the internet, browse and sometimes use a word processor.

I recall seeing a lot of discussion about unreliable wireless connections when wireless is installed with Ubuntu.  Apparently, some people get better wireless results if they omit the wireless from the install, and then use apt-get, the Software Center, or Synaptic to install the wireless stuff later.  I don't know for sure because I don't have any wireless hardware - I'm just summarizing what I have read.

You might consider Puppy Linux.  I have an old Dell with 256 MB of RAM and my choice was to scrap it or use it.  I found that Puppy Linux works well on this machine but it does have one drawback - Puppy Linux is a single user system.  That user must necessarily be root.  So you must run the system with full privilege at all times.  This is OK if you are careful and you know what you are doing. Having two systems that can talk to each other is great - I have used ssh to access one system from the other in order to make software repairs.

quadproc

---

