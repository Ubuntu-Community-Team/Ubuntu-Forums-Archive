---
title: "Extremely poor graphics and video quality"
date: 2010-10-07
forum: General Help
---

### Post by Shishant on 2010-10-07
Hello,

I just recently migrated from windows 7 to ubuntu as a full time user, But I am very much disappointed with the video and graphics quality.

I am using ATI / AMD  proprietary FGLRX graphics driver which were recommended by ubuntu.

And viewing videos in full screen mode, the video quality is worst and it also slows down computer alot, even if there are no other apps running, I used win7 from last 8 months and on this same machine I never had this problems and I am sure my graphic card is working well maybe the ubuntu decoder has some bug and needs attention as this same problem is even faced by other users using graphic cards .

You can see the image quality :
[IMG]http://i52.tinypic.com/2q1yq8i.png[/IMG]


//////// EDIT ////////

Well I found out that the quality is worst while using firefox, but quite better in chrome but still its not upto the mark. Should I expect anything in near future because I am really looking to switch to ubuntu?

---

### Post by Mark Phelps on 2010-10-07
You sure you're using the proprietary driver?  Open a terminal and enter "sudo fglrxinfo".  If it says command not found, or something like that, you're not actually using the proprietary driver.

As to video quality, installing the proprietary driver is what we generally recommend.  If you've already done that, don't know of anything else you can do to improve the video quality.

---

### Post by mastablasta on 2010-10-07
Linux ATI drivers are in the making. they are not fully optimised yet. try using open source drivers, see if that helps.
 
By the way you didn't say exactly what graphics card you are using.

---

### Post by TBABill on 2010-10-07
I would suspect you installed the driver but the system is still using a vesa or open source driver not quite optimal for your hardware, but just a guess.

---

### Post by Shishant on 2010-10-07
> **Mark Phelps said:**
> You sure you're using the proprietary driver?  Open a terminal and enter "sudo fglrxinfo".  If it says command not found, or something like that, you're not actually using the proprietary driver.

As to video quality, installing the proprietary driver is what we generally recommend.  If you've already done that, don't know of anything else you can do to improve the video quality.

Here is there screenshot: 
[IMG]http://a.yfrog.com/img704/8072/selection004h.png[/IMG]

> **mastablasta said:**
> Linux ATI drivers are in the making. they are not fully optimised yet. try using open source drivers, see if that helps.
 
By the way you didn't say exactly what graphics card you are using.

I will surely give it a shot and let you know

> **TBABill said:**
> I would suspect you installed the driver but the system is still using a vesa or open source driver not quite optimal for your hardware, but just a guess.

How to check it?

---

### Post by Quackers on 2010-10-07
If you go to System > Admin > Additional Drivers is the driver present AND activated?

---

### Post by Shishant on 2010-10-07
> **Quackers said:**
> If you go to System > Admin > Additional Drivers is the driver present AND activated?
System > Administration > Hardware Drivers shows this:

[IMG]http://img1.imagehousing.com/65/e2bb0b7f165f88a67a056ee81f6b67ef.png[/IMG]

---

### Post by Quackers on 2010-10-07
Yep, that's what it should say. What resolution are you currently running?

---

### Post by coffeecat on 2010-10-07
I think your problem may be that you are using the proprietary driver. I'm posting from 10.04 with an ATI HD4350 card using the open source driver and compare my Firefox-google screenshot with yours. The open source driver gives me adequate 3d acceleration for compiz and a nice, clear screen display.

If your resolution is correct and you want to uninstall the proprietary driver and revert to the open source one, here are some instructions:

[https://help.ubuntu.com/community/RadeonDriver#Removing%20the%20proprietary%20fglrx%20driver]("https://help.ubuntu.com/community/RadeonDriver#Removing%20the%20proprietary%20fglrx%20driver")

---

### Post by Shishant on 2010-10-07
> **Quackers said:**
> Yep, that's what it should say. What resolution are you currently running?
I am using Dell Monitor: G2410, Resolution: 1920 x 1080, Refresh Rate: 60Hz, Connector: DVI

---

### Post by LowSky on 2010-10-07
> **coffeecat said:**
> I think your problem may be that you are using the proprietary driver. I'm posting from 10.04 with an ATI HD4350 card using the open source driver and compare my Firefox-google screenshot with yours. The open source driver gives me adequate 3d acceleration for compiz and a nice, clear screen display. 

the proprietary driver should actually be better in the graphics department

open up ATI's Catalyst and check your settings. I'm betting something there is set wrong

---

### Post by coffeecat on 2010-10-07
> **LowSky said:**
> the proprietary driver should actually be better in the graphics department

Grabs throat, falls about floor coughing violently with tears streaming down face!

Not always. :(

---

### Post by Quackers on 2010-10-07
I have a Nvidia card so haven't had the problem but am I correct in thinking that the FGLRX has been problematical lately?

---

### Post by Shishant on 2010-10-07
I removed the driver from System > Adminstartion > Hardware Drivers but now from where should I install open source drivers? Because when I open Hardware drivers there are no other options available it just shows the same proprietary driver and "Activate" button

---

### Post by coffeecat on 2010-10-07
> **Shishant said:**
> I removed the driver from System > Adminstartion > Hardware Drivers but now from where should I install open source drivers? Because when I open Hardware drivers there are no other options available it just shows the same proprietary driver and "Activate" button

You don't need to install the open source driver. It is already there. But follow the link I posted. The fglrx driver is notorious for leaving bits of itself everywhere. Simply disabling it in Hardware Drivers is sometimes not enough.

But you should have checked the FGLRX driver settings were correct before uninstaliing it. You posted the resolution of your monitor but not the resolution the driver was giving you.

**Edit:** Apologies. The Community documentation page I posted earlier is not the best for uninstalling the fglrx driver. Here's a better one:

[https://help.ubuntu.com/community/RadeonHD#Preparation](https://help.ubuntu.com/community/RadeonHD#Preparation)

---

### Post by cottfcfan on 2010-10-07
The reason Firefox looks poor is that it needs the "smooth scaling ppa" adding, I have the same problem.
Go to System, Administration, Synaptic.
Click Settings, Repositories, Other Software, Add,
ppa:firefox-smooth-scaling/ppa
Then close, Reload and install upgrades.
Open Firefox and Fonts should be fine.

---

### Post by Shishant on 2010-10-07
> **cottfcfan said:**
> The reason Firefox looks poor is that it needs the "smooth scaling ppa" adding, I have the same problem.
Go to System, Administration, Synaptic.
Click Settings, Repositories, Other Software, Add,
ppa:firefox-smooth-scaling/ppa
Then close, Reload and install upgrades.
Open Firefox and Fonts should be fine.
(I re-activated the driver to test your tweak)

It actually solved the firefox issue, but is there any idea what should be done for bad video qualities? When playing videos on youtube the system almost hangs with bad quality and playing videos on disk with any video player the quality is also unacceptable.

---

### Post by cottfcfan on 2010-10-07
shishant...
Which version of Ubuntu are you using?
The reason I ask is that 10.10 is out in 3 days, ive been using it for a while with the open source drivers.
Fonts seem sharper, particularly the new Ubuntu Font.
I'm using a radeon ati card same as you and all is fine.

---

### Post by Shishant on 2010-10-07
I am using 10.04, so the final version of 10.10 will be released after 3 days? And I have already installed a ton of softwares so would you recommend upgrading or fresh install?

I must admit by the way the fonts just look awesome even on 10.04 I like it more than win7 (btw I am using Sans & Monospace)

I will surely give Ubuntu font a try.

---

### Post by cottfcfan on 2010-10-07
Fresh installs are always best, but its upto you.
BTW the video problem is probably flash related.
Flash is notoriously poor in Linux although it is improving, when i watch the BBC iplayer video can be choppy. It is slightly better on 10.10, but for me personally it renders better with the open source drivers rather than FGLRX.

---

### Post by TBABill on 2010-10-07
Are you using Gnash or Adobe Flash? Gnash is just a bad flash player and you should see improvement with Adobe Flash if you are not currently using it. And make sure you don't have more than a plugin conflicting with another (i.e., 2 plugins to do one job such as having Gnash and Flash or OpenJava and SunJava).

---

