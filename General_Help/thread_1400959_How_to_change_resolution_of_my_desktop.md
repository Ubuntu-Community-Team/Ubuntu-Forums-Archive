---
title: "How to change resolution of my desktop?"
date: 2010-02-07
forum: General Help
---

### Post by madmax.santana on 2010-02-07
I have recently installed Ubuntu on an old system. I've never had to change the resolution of my Ubuntu desktop before. But now, GNOME appears in 800x600 resolution. I want to change it but I don't know how... Could anyone guide me please?

---

### Post by ron999 on 2010-02-07
Hi
System > Preferences > Display

---

### Post by madmax.santana on 2010-02-07
There is a problem. The Display Settings menu shows a maximum 800x600 resolution... I want to make it 1024x768. And I can do that with the same hardware in MS Windows. Is there a possibility that I can increase my desktop resolution in Ubuntu as well.

---

### Post by NightwishFan on 2010-02-07
Please tell us what your graphics hardware actually is.
```
sudo lshw -C display
```

---

### Post by coldfusion1313 on 2010-02-07
you might need to install your restricted video card drivers.

---

### Post by madmax.santana on 2010-02-08
I executed the lshw command and came up with this output. It is an onboard Graphics Card which came with my Intel GVWB-915 desktop board... On windows I have had to install drivers to correct my problem but in Linux the drivers are pre-installed and yet the problem remains.

Here is the output to the command which 
 				 				[NightwishFan]("http://ubuntuforums.org/member.php?u=484925") 				 				 			
  			 directed me to run.[URL="http://ubuntuforums.org/member.php?u=484925"]
[/URL] 				 				 			
  			
> *-display               
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:ff280000-ff2fffff ioport:ec00(size=8) memory:d0000000-dfffffff(prefetchable) memory:ff240000-ff27ffff

---

### Post by NightwishFan on 2010-02-08
I have heard you can manually edit your Xorg.conf to get other resolutions, though the exact method is beyond my knowledge. If I learn anything I will get back to you. Until that time look for ways to edit Xorg.conf with Intel cards.

---

### Post by madmax.santana on 2010-02-10
I have tried many many possibilities. I end up either to no effect or the system crashed...

In my X11 directory, there was no Xorg.conf. So I created one. And when I restarted, XWM crashed, saying that it could not "parse" files...

I also tried downloading the 915resolution package which repairs the screen resolution automatically (supposedly). But I didn't know how to use it. There was a readme file I tried to get help from but still I am blank as to how to change my screen resolution through that tool.

I would also like to mention that I am installed a Sun OpenSolaris distribution on the same drive, just for testing. As it appears to me, OpenSolaris uses the same interface as Ubuntu i.e. gnome and it has many things in common with Ubuntu. Overall, it looked to me like an overextended derivative of Ubuntu, like probably Linux Mint. Whatsoever, Solaris gave me a correct 1024x768 resolution, without any makeshift repairs. But I am blank as to how and why...

Anyway, all fellas, please help me there since this 800x600 res is very annoying on such a large monitor... Please, if anyone with the same system has faced and got rid of the same problem in past, enlighten me. I am very annoyed and desperate... :) Thank you

---

### Post by NightwishFan on 2010-02-10
Here are some answers about resolution:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by theozzlives on 2010-02-10
Here's a "dirty" fix that worked for me once. Boot off the Jaunty CD, if you don't have one burn Hardy. If the display is fine on the live CD, copy the xorg.conf from the X11 folder on the CDs image to the X11 folder on your hard drive (you may need root privileges).

I'm not saying it'll work, but it did for me once.

---

### Post by madmax.santana on 2010-02-10
Hahahahaha!!! @theozzlives, THAT WAS A PRETTY COOL TRICK. Really I likes it. It didn't work though. But I like the idea. Looks like my kind of thing. Exterminating the root instead of using a weed-killer. Nice. However as it appears, the xorg.conf file in my Ubuntu 8.10 Disk cotained only default information. Just 
Machine "ThisMahine"
Method "ThisMethod"
type of lame configuration. I knew it wont work before I even put it to use. But anyway, I did it and it happened as I had anticipated. No changes absolutely. 
There is this thing though, now I know Ubuntu 8.10 LTS doesn't show this anomaly with my hardware. So my hardware is absolutely capable of what I am trying to do.

> [COLOR=DeepSkyBlue][I]Another thing. I am going to install Ubuntu 8.10. I know it is bad motivation, trying to avoid errors instead of facing them. ;) But nothing seems more appropriate. You must know how annoying it is to watch movies and view webpages at 800x600.:D Literally, I have to scroll left and right to read your forum message. So that's it. Ubuntu 8.10

But please let me know when you have a solution for that. I shall really miss Karmic.[/I][/COLOR]

[COLOR=Red]Guys cancel that!!! I am not going to install Ubuntu 8.10. I have solved my problem... Just a wild hit though. As one friend [/COLOR][NightwishFan]("http://ubuntuforums.org/member.php?u=484925")[COLOR=Red] suggested a few posts back that I could change the Xorg.conf file manually... And also, the same guy gave a link which explained how xorg.conf works. I worked on these principles and got the problem sorted out... For anyone else ever having the problem, editing xorg.conf file is a neat solution ad it is not that difficult.

[/COLOR]```
$ cvt 1024 768
```[COLOR=Red][COLOR=Black]
gave me the required parameters for the resolution. It was a long line of bla bla which I know nothing about and don't care either.

Then I when to tty1 by Ctrl+Alt+F1 and stopped the gdm. Then I ran
[/COLOR][/COLOR]```
$ Xorg -configure
```[COLOR=Red][COLOR=Black]
to generate the default xorg.conf file by name "xorg.conf.new" for my hardware which was put in my home folder. I edited that file and in Screen section added the output of cvt wherever the Display Subsection appeared. Then I saved the file, made it executable by chmod and replaced the old xorg.conf in my /etc/X11 dir. Then rebooted and got a 1024x768 resolution. Perfecto.

I know it looks like a mess of things but I am sure it is better than many other methods.
[/COLOR][/COLOR][COLOR=DeepSkyBlue][/COLOR]

---

