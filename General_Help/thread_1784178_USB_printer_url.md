---
title: "USB printer url"
date: 2011-06-16
forum: General Help
---

### Post by Yepi on 2011-06-16
Hi, I am a new Ubuntu user and I am getting really frustrated with setting up my plotter, I had it working perfectly fine and for some reason it doesn't work any more. I have searched for about 2 hours on the web,forums etc

I have set it up the same way as previously with no luck.

I think the problem is in the printer>properties it doesn't show a URL, it says usb://unknown/.

I am using a usb-parallel cable to connect the plotter.

I have set it up through a usb-serial aswell which gives me a URL serial:/dev/ttyS0?baud=115200 so I am expecting something like that or something like /dev/ttyUSB some number or usblp0

Would really appreciate some help

---

### Post by sidzen on 2011-06-16
Check out [**[SIZE=2]this post[/SIZE]**]("http://www.linuxquestions.org/linux/answers/Hardware/Slackware_12_0_Installing_Canon_Pixma_iP1700"), which should be similar to what you want to do!

First, uninstall all printers and logoff and logon.  Then follow the guide above.

Hope this works for you!

If not, include your plotter make and model number.

---

### Post by Yepi on 2011-06-17
Hi, thanks for the reply.

The post refers to canon printers and their specific files so I don't see how it will work with my plotter. My plotter is a Roland DXY 980. 

I went into the cups interface and tried to find Roland but it is not there. I tried to restart cups, just gave me a permission denied error.

Previously it worked just fine by adding a generic printer and using the 'Raw queue' option and that was it, I could then use a program called TuxPlot to get plotting.

I think an update messed things up because I have not done anything myself to it.

---

### Post by Yepi on 2011-06-18
I removed completely my Ubuntu from my desktop and installed a fresh copy on my laptop, tried to set the plotter as before and again no success. 

Below is the link to the video that I used to set it up first time which worked, tried the same this time and it didn't work

[HTML]http://www.youtube.com/watch?v=Seaje_YJ5sU[/HTML]

---

### Post by sidzen on 2011-06-20
All I was able to find was [**here**]("http://www.linuxforums.org/forum/newbie/21573-roland-stika-sx-12-driver-vinyl-cutter.html")
Hope it helps!

---

